# Chapter 11 : Return nice error message if payload is not valid JSON

AU : I sent invalid JSON payload and in return I did not get valid JSON response. My mobile application crashed because I was expecting response to be valid JSON.

AB : Do you know how Rails parses JSON data.

AU : Nope.

AB : The thing is that if the payload is invalid JSON then the request does not even hit the controller.

AB : Rails attempts to parse the payload and since the paylaod is invalid it blows up up in the middleware stack.

AU : I see.

AU : Well we can write a custom middleware which will catch the exception and will return a valid JSON data.

AB : I have no idea how to do that.

AU : Ok. Here is my attempt to build it.

``` ruby
# app/middleware/catch_json_parse_errors.rb

class CatchJsonParseErrors

  def initialize app
    @app = app
  end

  def call env
    begin
      @app.call(env)
    rescue ActionDispatch::ParamsParser::ParseError => exception
      content_type_is_json?(env) ? build_response : raise(exception)
    end
  end

  private

  def content_type_is_json? env
    env['CONTENT_TYPE'] =~ /application\/json/
  end

  def error_message exception
    "Payload data is not valid JSON. Error message: #{exception}"
  end

  def build_response
    [ 400, { "Content-Type" => "application/json" }, [ { error: error_message(exception) }.to_json ] ]
  end

end
```

AU : Now we need to use this middleware. Here is how we can ask Rails to use this custom middleware.

``` ruby
# config/application.rb

require File.expand_path('../boot', __FILE__)
require 'rails/all'
Bundler.require(:default, Rails.env)

module Wheel
  class Application < Rails::Application
    config.middleware.insert_before ActionDispatch::ParamsParser, 
                                    "CatchJsonParseErrors"
  end
end

```

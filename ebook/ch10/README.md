# Chapter 10 : Response should be valid JSON even when things go wrong

AU : I'm getting an error. And the response payload is not valid JSON.

AB : What's the returned status code ?

AU : 500.

AB : Well that means something went wrong on the server side. What can I do.

AU : Build API in such a manner that even in case of error valid JSON is returned.

AB : How do I do that.

AU : With Rails's it is super easy.


``` ruby
class Api::V1::BaseController < ApplicationController

  rescue_from Exception, with: :handle_api_exceptions

  private

  def handle_api_exceptions exception
    log_exception exception

    error_message = 'Something went wrong. Please try again later.'
    respond_with_error(error_message, 500)
  end

  def respond_with_error(message, status = 500)
    render json: { error: message }, status: status
  end

  def log_exception exception
    Rails.logger.info exception.class.to_s
    Rails.logger.info exception.to_s
    Rails.logger.info exception.backtrace.join("\n")
  end

end
```

Now anytime there is an exception it is guaranteed that valid JSON will be the response.



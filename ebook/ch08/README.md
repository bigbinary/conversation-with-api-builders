# Chapter 8 : No need to have success key in response.

I have seen a lot of APIs pass `success` key to indicate if the request was successfully handled or not. There is no need to do that. Response status code should be used instead.

``` ruby
# do not do this. 
message = "No car was found for car_id #{params[:car_id]}."
render  json: { success: false, error: message }, status: :not_found
```


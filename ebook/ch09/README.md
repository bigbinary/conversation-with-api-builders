# Chapter 9 : Do not use redirect in API

``` ruby
   # do not do this
  def destroy
    .... 
    @user.destroy
    redirect_to :back
  end
```

In the above case `redirect_to :back` does not mean anything when you are dealing with API. The correct version would be 

``` ruby
  def destroy
    .... 
    @car_alert.destroy
    render head: :no_content, status: :ok
  end
```






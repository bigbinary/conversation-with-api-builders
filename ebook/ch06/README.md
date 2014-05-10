# Chapter 6 : Use 404 when record is not found

AU : When a record is not found then error message should be clear about what record is not found.

AU : And use status code **404 to indicate that record was not found**.

AB : I am used to writing code like `current_user.cars.find params[:car_id]`. It raises an exception when record is not found.

AU: Yeap. That code needs slight tweaking when it is used inside an API.  Rather than raising an excpetion send a clear error message when record is not found.

AB : This is what I have right now.

``` ruby
class Api::V1::CarAlertsController < Api::V1::BaseController

  before_action :load_car

  private

  def load_car
    @car = current_user.cars.find params[:car_id]
  end

end
```

AB : In the above code the issue is that if there is no car matching `params[:car_id]` then above code would raise `ActiveRecord::RecordNotFound` exception.  

AU : Above code can be refactored to following code.

``` ruby
class Api::V1::CarAlertsController < Api::V1::BaseController

  before_action :load_car

  def show
    if @car
      ...
    else
      message = "No car was found for car_id #{params[:car_id]}."
      render  json: { error: message }, status: :not_found
    end
  end

  private

  def load_car
    @car = current_user.cars.find_by_id params[:car_id]
  end

end
```


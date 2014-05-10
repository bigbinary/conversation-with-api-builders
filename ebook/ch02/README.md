# Chapter 2 : Use 400 when the request payload is not valid

AB : It's fixed. Now you will get 400.

AU : But that's wrong too.

AB : Now what's your problem.

AU : Send 400 when data is not **syntactically correct**.

AB : What does that even mean.

AU : Let me elaborate.

AU : In order to create a user I'm sending the user data in JSON format.  Right ?

AB : Right.

AU : And the JSON that I'm sending is valid JSON. Right ?

AB : Right.

AU : Then you can't send 400. ***Because 400 is when the data itself is malformed.***

AB : I see. So if the payload is not valid JSON then I could send 400.

AU : Right.

AU : If the API accepts xml and the xml is not well-formed then you can send 400.

AB : Got it.

AB : So what status code I should send in your case when email is taken.

AU : Let's talk about it tomorrow.


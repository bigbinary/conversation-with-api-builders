# Chapter 1 : Use 200 when it is all good

**AB** is short form of **API Builder**.

**AU** is short form of **API User**.

AU : AB I have a problem.

AB : What's wrong.

AU : I sent a request to the API to create a user. But I do not see the newly created user. 

AB : Let me check.

AB : The email address that you sent is already taken.

AU : Hmmm..but I got 200 as the response status code.

AB : Forget about the response code. You need to check the payload. I sent the error message as "error" key.

AU : If the system could not create the user then why did it return 200 as response status.

AB : Because I always send 200 and I put the error message in the error key.

AU : You are doing it wrong. http status code is your friend. There are many status codes to indicate different types of errors.

AU : A response status code in the range of 400-499 indicates that the request was not processed successfully.

AU : A 200 response status code means that the request was processed successfully. So if the record could not be created then do not send 200.

# Chapter 7 : Use 500 when there is a processing error

AU : Hi there. Long time no see.

AB : Yes I was busy. The API code is in production now.

AU : I noticed. I got error message that something went wrong.

AB : yes. I'm working on it.

AU : **If something goes wrong then you should send response code 500.**

AU : It means that something unexpected happened. Like an exception was raised or database could not be connected. 

AU : Even in the case of 500 system should take utmost care that returned value is valid JSON or xml. Otherwise the client might run into problem while parsing the response body.

# Chapter 3 : Use 422 when the data is not valid

AU : ***422 should be used when the data is syntactically correct but semantically incorrect.***

AB : You sure love fancy words.

AB : Last time you talked about data being **syntactically correct**. 

AB : And now you are talking about **semantically incorrect**. Why can't you speak simple english.

AU : "Semantically" simpley means business wise.

AU : It's possible that the payloadl sent by the client is valid JSON but it is not complying with the business rules.

AU : For example in order to create a user you need name. If the payload does not provide name then it is an example of data being valid JSON data but "business-wise" it is not valid. 

AU : So in other words the payload is "syntacticaly correct" but "semantically incorrect".

AB : That's good to know. I will fix the code.

# Chapter 4 : Use 401 when user is not authenticated

AU : API that was working last night is now returning 422.

AB : Did you check the error message.

AU : Yes I did. And it says "you are not authenticated".

AB : Yes. I'm enforcing the rule that you need to be authenticated to create a user.

AU : You are enforcing the rule that's alright but you are returning 422.

AB : Now what's the problem. You yourself said that if the data is "semantically incorrect" then send 422.

AU : Yes. I said that. Now you tell me if the data then I sent is valid JSON or not.

AB : The data is indeed valid JSON. But my business rule is that you need to be authenticated. 

AU : To enforce authenticatin related business rules use response status code of 401.

AU : ***Use 401 when resource needs to be authenticated.***

AB : Cool. I'm going to fix the API now.

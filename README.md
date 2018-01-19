# springboot-oauth2-jwt-jpa
# Using JWT with Spring Security OAuth

# App example implements oauth2-server and resource api to consume this server.
# Token type Bearer
# Token format JWT

Spring-Boot-OAuth2-JWT-MySQL

Git URL : https://github.com/cpapidas/Spring-Boot-OAuth2-JWT-MySQL

https://www.youtube.com/watch?v=vML-NZET_Ss

Full Security Login System with Spring Boot
This project contains all the configuration about an authentication and authorization system. We are using spring boot framework, spring security, spring oauth token and mysql. Cause we want ours projects be scalable as they can we are using the JWT token key for authentication with oauth2, this means that we don’t need sessions and session storage system so our application will work faster and better even in cloud server without any configuration.

Features
•	User Auhtentication

•	User Authorazation

•	Account Registration

•	Forgot Password (Not Ready yet)

The concept of OAuth2 authentication and JWT

OAuth1
OAuth1 has 3 steps and one loop. Check the diagram bellow and you will understand what we define as step and loop. 

loop: We can say that a loop is a request between client and server

step: As a step we define the blocks of algorithm “mythology”

In login system client and server have to follow those steps

•	Sent the username and password to server via post request
•	server will send to the client the access token
•	client now have to store the access token into cookies or local storage
When client now want to get all products (for example)

•	Client should send the access token as header parameter
•	server parse all request the check if the header access token field is correct
•	then return all products

OAuth2
OAuth2 is more complex that OAuth, it has 3 loops and 3 steps in each loop.


In the first loop

•	client send the username and the password throw get request
•	server return the refresh token. Refresh token is something that give the ability to user to request for re access token. The main difference between them are that the refresh token exist for a lot longer and but the access token is the only one that give to you the ability to have real access to the application.
•	client get the refresh token and have to store it to cookies or local storage
The second loop

•	client is ready to request for an access token, so it sends to server a get request with the refresh token to get the access token.
•	server check for the refresh token and if this is correct then
•	return to client the access token
The third loop

•	Now user have to send the access token via get or as header parameter
•	Server analyze the access token and if this is correct then
•	return the request to user
Database

As database we are using the MySql, if you want to run the project you want edit the resource/config/application.properties file and add your database settings. After that import the databse.sql file that exists in root directory

How to run it

•	First Download the project
•	Install all Maven Dependencies
•	Edit the resource/config/application.properties file and add your properties (Mysql Database, Gmail - Email Sender)
•	After that import the Databse.sql file that exists in root directory
•	Run the project by spring-boot:run agian

How to use it

To run this example you must import the databse file that exists in root directory

-First ask for a access token curl -X POST -vu clientapp:123456 http://localhost:8080/oauth/token -H "Accept: application/json" -d "password=papidakos123&username=papidakos&grant_type=password&scope=read%20write&client_secret=123456&client_id=clientapp"



In Google Postman extension below steps

1.	POST Request.
http://localhost:8080/oauth/token?password=papidakos123&username=papidakos&grant_type=password&scope=read%20write&client_secret=123456&client_id=clientapp

http://localhost:9094/oauth/token?grant_type=password&password=kalpesh1988&username=kalpesh


In Authorization Tab select Type as Basic Auth
Username= clientapp
Password=123456

It will receive below response as shown in below screen.
{
    "access_token": "eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmVzdHNlcnZpY2UiXSwidXNlcl9uYW1lIjoicGFwaWRha29zIiwic2NvcGUiOlsicmVhZCIsIndyaXRlIl0sImV4cCI6MTUwMzUyNTM3OSwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6ImQ2NmE5N2JiLWIyNGQtNGVjZC05NTJmLTc1ZmFhYmExMjc5YSIsImNsaWVudF9pZCI6ImNsaWVudGFwcCJ9.3eMLibIPc5NRa3ha4_01OlKk3g6hS6qeRnfskgOGqWs",
    "token_type": "bearer",
    "refresh_token": "eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmVzdHNlcnZpY2UiXSwidXNlcl9uYW1lIjoicGFwaWRha29zIiwic2NvcGUiOlsicmVhZCIsIndyaXRlIl0sImF0aSI6ImQ2NmE5N2JiLWIyNGQtNGVjZC05NTJmLTc1ZmFhYmExMjc5YSIsImV4cCI6MTUwNjA3NDE3OSwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6IjQ4YzNkYjIwLWVmMGYtNDVhZC04NDRlLTc2ZjNjZjY3YTRjNSIsImNsaWVudF9pZCI6ImNsaWVudGFwcCJ9.eIo4-nQx1wnROvp6aFCQkMrQKFnaYE_o7fwLZ-XFpxs",
    "expires_in": 43199,
    "scope": "read write",
    "jti": "d66a97bb-b24d-4ecd-952f-75faaba1279a"}
-Now Try with postman get data from secure api uri. Don't forget to replace the headers token with your access token  prefix as bearer which get in tocken_type

Below is very useful working example


https://github.com/vit0r/springboot-oauth2-jwt-jpa#for-testing-using

see requests_py for how to run 

oauth2 APIs
/oauth/authorize (the authorization endpoint), 
/oauth/token (the token endpoint), 
/oauth/confirm_access (user posts approval for grants here),
 /oauth/error (used to render errors in the authorization server),
 /oauth/check_token (used by Resource Servers to decode access tokens),
 and /oauth/token_key (exposes public key for token verification if using JWT tokens).

1.	POST
http://localhost:9094/oauth/token?grant_type=password&password=kalpesh1988&username=kalpesh
 Authorization type=Basic Auth
Username=Client Id (Kalpesh)
Password=scret (kalpesh123)

2.	Post. http://localhost:9094/oauth/token?grant_type=refresh_token&refresh_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOlsiQ0RMLUlGUyJdLCJ1c2VyX25hbWUiOiJrYWxwZXNoIiwic2NvcGUiOlsib3BlbmlkIl0sImF0aSI6IjlmZjJjNDhiLWMwNzUtNDk5NS04MjI0LTJjMmNiZTRlY2Q5NCIsImV4cCI6MTUwNjY2MTYwOCwiYXV0aG9yaXRpZXMiOlsiUkVBRCIsIldSSVRFIl0sImp0aSI6IjllZDI1ZWE5LWZiYzktNGQwYi1hZDY5LTViYTQwODFhZmZmOSIsImNsaWVudF9pZCI6ImthbHBlc2gifQ.oYVzzOrec8Qe1vfNaxfm_SPfHJoEwcbZYD5FOmmXp2M
 Authorization type=Basic Auth
Username=Client Id (Kalpesh)
Password=scret (kalpesh123)

3.	POST
http://localhost:8070/oauth/check_token?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOlsiQ0RMLUlGUyJdLCJ1c2VyX25hbWUiOiJrYWxwZXNoIiwic2NvcGUiOlsib3BlbmlkIl0sImV4cCI6MTUwNDA3NDU1MywiYXV0aG9yaXRpZXMiOlsiUkVBRCIsIldSSVRFIl0sImp0aSI6IjQxOTEzYzAwLWM1NWEtNGJlMy05YWYzLWE1M2JiMWM2OTkwYyIsImNsaWVudF9pZCI6Im1hbmFnZXIifQ.6_DXyyDznD0dEtm8-RIC991i0WGUHELD73i2mtSOCh0

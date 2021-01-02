# DockerWithHttps  

A playground project to run a .Net Core WebApi project in a Docker container, using Https.  
  
### Generate the app certificate  
*dotnet dev-certs https -ep $HOME/.aspnet/https/WeatherApi.pfx -p "mypass"*
  
### Note:  
I tested this on MacOS, and was not able to use user-secrets to get the certificate password.  
Also .Net Core is not able to automatically find the certificate itself.  
  
To make this work, I add to use the 2 additional environment variables in the docker-compose file:  
*ASPNETCORE_Kestrel__Certificates__Default__Path: "/root/.aspnet/https/WeatherApi.pfx"*  
*ASPNETCORE_Kestrel__Certificates__Default__Password: "mypass"*  

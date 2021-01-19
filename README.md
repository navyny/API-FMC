# API-FMC
Firepower Management Center API


With Token Based Authentication you obtain a token by providing your username and password. You use this token to access an HTTP service for a limited time period without the need for the username and password with every request. In other words, to eliminate the need for authenticating with your username and password with each request, you replace user credentials with a uniquely generated access token, which you use for accessing resources for up to 30 minutes and can refresh up to three times. 

![image-1](https://user-images.githubusercontent.com/16725668/105071594-a868ac80-5a39-11eb-8320-40e478cc8899.jpg)




How to get "X-auth-access-token" that will be added to header in all future requests:

Example:
import requests

url= https://url="https://fwm-aln-us-1.nsnet.local/api/fmc_platform/v1/info/serverversion"
headers = {
           'X-auth-access-token' : "2aacsdafjdlkjfdlskfdsolhfalksaldksalklsa",
           }
           
response = requests.request("GET", url, headers=headers,verify=Flase)

print(response.text)


How to get the token first using usernme & passowrd:

curl -k -L -d '{"username":"root","password":"default"}' https://address.of.opengear/api/v1/sessions/
curl -k -L -d '{"username":"root","password":"dxsfsdf"}' https://rm-wst-us-mgr.netscout.com/monitor/dashboard/api/v1/sessions/


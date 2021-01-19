# API-FMC
Firepower Management Center API


With Token Based Authentication you obtain a token by providing your username and password. You use this token to access an HTTP service for a limited time period without the need for the username and password with every request. In other words, to eliminate the need for authenticating with your username and password with each request, you replace user credentials with a uniquely generated access token, which you use for accessing resources for up to 30 minutes and can refresh up to three times. 

![image-1](https://user-images.githubusercontent.com/16725668/105071594-a868ac80-5a39-11eb-8320-40e478cc8899.jpg)


###How to get the token first using usernme & passowrd:

```
import requests
import urllib3
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
url="https://fwm-aln-us-1.nsnet.local/api/fmc_platform/v1/auth/generatetoken"

headers = {
    'Content-Type' : "application/xml",
    'Authorization' : "Basic YS1uYXZlZW4udmFsbGFiaGFuZW46U3RvaWNsaWZlIzE5"
    }

response = requests.request("POST", url, headers=headers, verify=False)

print(response.headers['X-auth-access-token'])
print(type(response.headers))

```

###USING THE X-auth-access-token from Above and using GET method to obtain Server version

```
url= "https://fwm-aln-us-1.nsnet.local/api/fmc_platform/v1/info/serverversion"
headers = {
           'X-auth-access-token' : response.headers['X-auth-access-token'],
           }
           
response = requests.request("GET", url, headers=headers, verify=False)

print(response.text)
```


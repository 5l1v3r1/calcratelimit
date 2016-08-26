# Calcratelimit

##Introduction
Calcratelimit is a POC to provide calculcation based rate limiting. This can be of use for computation-heavy API calls. If a server has to perform a lot of computation for a certain API call, clients might overload the server. Calculation based rate limiting forces the client to also make heavy computations before being allowed to make the API call, mitigating the chance of overloading the server.

##How does it work?
1. A client has to make a call to the token endpoint. A random token is returned.
2. The client creates a additional token such that sha512(token + additional token) starts with the string '1337'
3. The client sends the original token + additional token to the API endpoint. Only if the two tokens create a hash that start with '1337' does the endpoint respond as it being a valid API call.

Only one token per ip per token/API call is allowed. Before every token call and after every API the database is cleared for that IP.

##Usage
The file calcratelimitClient.py contains a working POC for communicating with calcratelimit.graa.nl. This API only returns a success message, but works with the code from this repo.

##License
Calcratelimit is licensed under a Creative Commons Attribution-NonCommercial 4.0 International License. This means you are free to:

* Share — copy and redistribute the material in any medium or format
* Adapt — remix, transform, and build upon the material

**Under the following terms:**
* Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
* NonCommercial — You may not use the material for commercial purposes. 

For more information about the license see:
[https://creativecommons.org/licenses/by-nc/4.0/](https://creativecommons.org/licenses/by-nc/4.0/)

##Contact
For questions, bugs, or any contact involving Calcratelimit, email the email address: calcratelimit (attus) graa (dottus) nl
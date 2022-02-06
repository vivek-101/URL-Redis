# URL-Redis
Implementing URL shortening with Go and Redis as cache with Rate Limiting.

In this project I have tried to implement on of daily task used in any marketing or sales domain organisation which is URL Shortning using **Go, Redis, Docker, Docker-compose**. The backend is designed and developed in Golang while Redis is used as cache DB. I wanted to implement Rate limiting so i have also applied rate limiting to restrict the user for it and over burdening the server. I have wraped the application in Docker and using Docker compose the make a dev/prod ready containerised application.

The API Specs are below for raising the POST request <br>
	URL &emsp;&emsp;&emsp;&emsp;&emsp;&ensp;string   &emsp;&emsp;&emsp;&emsp;&ensp;     `json:"url"` <br>
	CustomShort &emsp; string &emsp;&emsp;&emsp;&emsp;&ensp; `json:"short"` <br>
	Expiry &emsp;&emsp;&emsp;&emsp;&ensp;time.Duration &emsp; `json:"expiry"` <br>
  
  
The response we will be getting in the below format(JSON)<br>
	URL       &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;  string  &emsp;&emsp;&emsp;&emsp;      `json:"url"`<br>
	CustomShort   &emsp;&emsp;&ensp;&nbsp;  string     &emsp;&emsp;&emsp;&emsp;   `json:"short"`<br>
	Expiry      &ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;    time.Duration &nbsp;&ensp;`json:"expiry"`<br>
	XRateRemaining   &ensp;&emsp;int    &emsp;&emsp;&emsp;&emsp;&emsp;  &nbsp;    `json:"rate_limit"`<br>
	XRateLimitReset  &nbsp; &emsp;time.Duration &nbsp;&ensp;`json:"rate_limit_reset"`<br>
  
  
For rate limiting, this logic applies to allow only 10 request per 30 min we can change it as per our requirement and the response shows how much time is left in resetting the request limiter.

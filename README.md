## To build this image
git clone https://github.com/billmetangmo/bidding.git

cd docker;docker build -t qopius/challenge:python-2.7-alpine-onbuild .

cd .. ; docker build -t qopius/challenge:python-2.7 .

## To run it
docker run --net host qopius/challenge:python-2.7

docker run --net host -e PORT xxxx qopius/challenge:python-2.7

docker run -e PORT xxxx:yyyy qopius/challenge:python-2.7

The ENV variables for the doker images are: RANDOMIZER_LOWER_VALUE; RANDOMIZER_LOWER_VALUE;IP; PORT


## To test the API
A service is deployed on GCP at IP/PORT 104.198.205.151/80

Don't forget to replace xx,yy,zz & name by thier corresponding values.

|      | Description |
| ---      | ---       |
| XX |  duration in seconds ( integer expected)   |
| ZZ     | price in euros       |
| YY     | bid id ( integer expected as returns through /start)      |
| name     | name (string expected)      |


curl -X GET http://104.198.205.151/start?duration=XX
 
curl -X GET http://104.198.205.151/bid/YY?amount=ZZ&name=name
 
curl -X GET http://104.198.205.151/getactualprice/YY
 
curl -X GET http://104.198.205.151/getwinner/YY
 


## To follow the bet in real-time

Check the logs of the server with contained detailed information about every update of the bid.

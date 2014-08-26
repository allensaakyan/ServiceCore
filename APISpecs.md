#  API Specifications
This specification will go through the API specs to be used by the front end of TapWater.

##  What is not covered
** Unhappy Paths
--* 404's, 500's, etc
** Messanging Section of the application

##  HTTP GET

| GET | Getting the content on the home page |
| ServiceCore/1.0/user/<id>/new_content |
| REQUEST: `""` | RESPONSE:  `{'img': string, 'title': string, 'content': string, 'id':string}` |
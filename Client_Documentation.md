# Client Documentation
Page2Pics is a resource to capture, store and deploy custom web screenshots for deployment in your own projects. It uses SpringBoot as the basis for its RESTful API service and AWS for secure storage of files.

## Deployment Instructions

To avoid any compatibility issues, a Dockerfile is provided. To run the application, simply type the commands:   

```$ sudo docker build -t bris/page2pics .```

```$  sudo docker run -p 8080:<port> bris/page2pics```


## API Documentation

### Home page
Name | Method | Description
-----|--------|------------
/ | GET | Returns Page2Pics home page (web page)

---

### View screenshot
Name | Method | Description
-----|--------|------------
/view | GET | Returns screenshot in-browser view (web page)

#### Request
##### Query Parameters
Name | Type | Required | Default value | Description
-----|------|----------|---------------|-------------
url | String | yes | None | The URL of screenshot source 
width | int | no | 1280 | The width of screenshot image
height | int | no | 720 | The height of screenshot image
name | String | no |  | The name of the screenshot
browser | String | no |  | The browser to use to create screenshot
delay | int | no | 0 | The delay between loading page and taking screenshot
expiry | int | no | 0 | //

#### Response
Returns "/view" web page displaying image of screenshot along with metadata.

---

### /api - POST
Name | Method | Description
-----|--------|------------
/api | PUT | Creates new screenshot entry in database or returns existing.

#### Request
##### Request body
Name | Type | Required | Default value | Description
-----|------|----------|---------------|-------------
url | String | yes | None | The URL of screenshot source 
width | int | no | 1280 | The width of screenshot image
height | int | no | 720 | The height of screenshot image
name | String | no |  | The name of the screenshot
browser | String | no |  | The browser to use to create screenshot
delay | int | no | 0 | The delay between loading page and taking screenshot
expiry | int | no | 0 | //

#### Response
HTTP Code | Content type | Description
----------|--------------|------------
200 | `application/json` | Screenshot database entry
400 | `application/json` | Error: no url specified

---

### New screenshot
Name | Method | Description
-----|--------|------------
/screen | GET | Creates new screenshot entry in database or returns existing.

#### Request
##### Query Parameters
Name | Type | Required | Default value | Description
-----|------|----------|---------------|-------------
url | String | yes | None | The URL of screenshot source 
width | int | no | 1280 | The width of screenshot image
height | int | no | 720 | The height of screenshot image
name | String | no |  | The name of the screenshot
browser | String | no |  | The browser to use to create screenshot
delay | int | no | 0 | The delay between loading page and taking screenshot
expiry | int | no | 0 | //

#### Response
HTTP Code | Content type | Description
----------|--------------|------------
200 | `application/json` | Screenshot database entry

---

### Fetch screenshot
Name | Method | Description
-----|--------|------------
/get | GET | Fetch existing screenshot from user database.

#### Request
##### Query Parameters
Name | Type | Required | Default value | Description
-----|------|----------|---------------|-------------
url | String | yes | None | The URL of screenshot source 

#### Response
HTTP Code | Content type | Description
----------|--------------|------------
200 | `application/json` | Screenshot database entry
404 | `text/html` | Couldn't find screenshot entry in database

---

### Delete screenshot
Name | Method | Description
-----|--------|------------
/delete | GET | Delete screenshot entry from database.

#### Request
##### Query Parameters
Name | Type | Required | Default value | Description
-----|------|----------|---------------|-------------
url | String | yes | None | The URL of screenshot source 

#### Response
HTTP Code | Content type | Description
----------|--------------|------------
200 | `text/html` | Screenshot entry successfully deleted

---

### Update screenshot
Name | Method | Description
-----|--------|------------
/update | GET | Update screenshot in database.

#### Request
##### Query Parameters
Name | Type | Required | Default value | Description
-----|------|----------|---------------|-------------
url | String | yes | None | The URL of screenshot source 
width | int | no | 1280 | The width of screenshot image
height | int | no | 720 | The height of screenshot image
name | String | no |  | The name of the screenshot
browser | String | no |  | The browser to use to create screenshot
delay | int | no | 0 | The delay between loading page and taking screenshot
expiry | int | no | 0 | //

#### Response
HTTP Code | Content type | Description
----------|--------------|------------
200 | `application/json` | Screenshot item updated and returned
404 | `text/html` | Failed update, no entry found

Takes screenshot url and optional descriptors.
Returns 404 error if no entry already in database
If entry in database, deletes old entry and replaces with new screenshot. Returns ok.

---

### Fetch username
Name | Method | Description
-----|--------|------------
/user | GET | Returns the user login name

#### Request

#### Response
Returns singleton map of user login name from their google/github account
```
{"name" : name}
```

---

### Account page
Name | Method | Description
-----|--------|------------
/account | GET | Retrieves the user account page

#### Request
OAuth2User authorisation key

#### Response
Returns "/account" web page

---

### Load screenshot
Name | Method | Description
-----|--------|------------
/snippet | GET | Display loading GIF, then display screenshot (web page)

#### Request
##### Query Parameters
Name | Type | Required | Default value | Description
-----|------|----------|---------------|-------------
url | String | yes | None | The URL of screenshot source 
width | int | no | 1280 | The width of screenshot image
height | int | no | 720 | The height of screenshot image
name | String | no |  | The name of the screenshot
browser | String | no |  | The browser to use to create screenshot
delay | int | no | 0 | The delay between loading page and taking screenshot
expiry | int | no | 0 | //

#### Response
Returns "/snippet" web page.







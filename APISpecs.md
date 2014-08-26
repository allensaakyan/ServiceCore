#  API Specifications
This specification will go through the API specs to be used by the front end of TapWater.

##  What is not covered
** Unhappy Paths
--* 404's, 500's, etc
** Messanging Section of the application

##  Hazyness
** Where the creation of the user is concerned, that's a bit hazy until I look into how the phone integrations work for native apps, but I gave it my best guess.

##  HTTP GET

**Description:** Getting the content on the home page

**Endpoint:** `ServiceCore/1.0/user/<id>/content/new`


**Variables:**
id = user account number / user token

**REQUEST:**
`""`

**RESPONSE:**
```javascript
{'img': string,
'title': string, 
'content': string, 
'content_id':string}
```

---

**Description:** Show the user what he has liked

**Endpoint:** `ServiceCore/1.0/user/<id>/content`


**Variables:**
id = user account number / user token

**REQUEST:**
```javascript
### Optional
{'pagination': int}
```

**RESPONSE:**
```javascript
{'likes': ['img': string,
           'title': string, 
           'content': string, 
           'id':string],
'pagination':int}
```

---

**Description:** Pulls up the friends the user has

**Endpoint:** `ServiceCore/1.0/user/<id>/friends`


**Variables:**
id = user account number / user token

**REQUEST:**
```javascript
### Optional
{'pagination': int}
```

**RESPONSE:**
```javascript
{'friends': ['img': string,
             'name': string, 
             'likes_shared': int],
'pagination':int}
```

---

**Description:** Gets user preferences and information

**Endpoint:** `ServiceCore/1.0/user/<id>`


**Variables:**
id = user account number / user token

**REQUEST:**
```javascript
""
```

**RESPONSE:**
```javascript
{'user_id': string,
'distance_pref': int
'age_min': int,
'age_max': int,
'min_likes': int}
```

## HTTP POST

**Description:** Creates a new user 

**Endpoint:** `ServiceCore/1.0/user/<id>`


**Variables:**
id = user account number / user token

**Header**
Possibly token instead of in URL and ServiceCore pulls all the data?

**REQUEST:**
```javascript
{'name': string,
'gender': string
'photo': string,
'zip': string,
'city': string}
```

**RESPONSE:**
```javascript
{'user_id': string} ## string because javascript cant handle big int
```

---

**Description:** Creates a new content post

**Endpoint:** `ServiceCore/1.0/user/<id>/content`


**Variables:**
id = user account number / user token

**REQUEST:**
```javascript
{'title': string,
'image': FileType (maybe url string)?
'content': string}
```

**RESPONSE:**
```javascript
{'content_id': string}
```

## HTTP PATCH

**Description:** User likes content

**Endpoint:** `ServiceCore/1.0/user/<id>/content/<c_id>`


**Variables:**
id = user account number / user token
c_id = content id

**REQUEST:**
```javascript
{'status': 'like'}
```

**RESPONSE:**
```javascript
{'img': string,
'title': string, 
'content': string, 
'content_id':string}
```

---

**Description:** User dis-likes content

**Endpoint:** `ServiceCore/1.0/user/<id>/content/<c_id>`


**Variables:**
id = user account number / user token
c_id = content id

**REQUEST:**
```javascript
{'status': 'dislike'}
```

**RESPONSE:**
```javascript
{'img': string,
'title': string, 
'content': string, 
'content_id':string}
```

---

**Description:** Update user preferences

**Endpoint:** `ServiceCore/1.0/user/<id>`


**Variables:**
id = user account number / user token
c_id = content id

**REQUEST:**
```javascript
{'user_id': string,
'distance_pref': int
'age_min': int,
'age_max': int,
'min_likes': int}
```

**RESPONSE:**
```javascript
""
```

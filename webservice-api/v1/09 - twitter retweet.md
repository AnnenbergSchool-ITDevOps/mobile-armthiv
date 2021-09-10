**Twitter Retweet**
----
  Retweet Twitter message with user email and message id. 
 

* **URL**

  /twitter/retweet

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`
   `id=[string]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"success":true,"posted":{"retweet":"success"}}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":{"retweet":"Sorry, that page does not exist"}}`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/twitter/userinfo",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```
  
  
* **example**

[https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/?email=xxx@gmail.com&id=1270095772227379209](https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/?email=xxx@gmail.com&id=1270095772227379209)


> Needs legit Twitter Username & ID?
> 
> - https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/?email=epj@asc.upenn.edu&id=1270095772227379209


___________

### CURL POST REQUEST

- using the known twitter `id_str=1022129459741245440`
- or is this known message ID? let's try `148477475`

```bash
curl -d "email=etiennej@upenn.edu&id=1270411880591437824" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/
```

- I get the following error on curl POST `{"success":true,"posted":{"user":"User email not found"}}`

- But if you go through URL I receive `{"success":true,"posted":{"retweet":"success"}}`
    - https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/?email=etiennej@upenn.edu&id=1270411880591437824

**OKAY SO I HAD TO UPDATE MY DEV APP ON TWITTER TO ALLOW READ & WRITE... I forgot I did read only for testing!**

On attempting to click again the link 
- https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/?email=etiennej@upenn.edu&id=1270411880591437824

- I get an error that the tweet ID isn't legit? `{"success":false,"posted":{"retweet":"No status found with that ID."}}`
- so try the available tweet in recMsg `1270411884051730435`
  - https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/?email=etiennej@upenn.edu&id=1270411884051730435
  - this now returns `{"success":true,"posted":{"retweet":"success"}}` and yes the retweet is there!

- Can we do it with CURL POST? Known ID in recMsg `1422748452065263617` for 20210805

```bash
curl -d "email=etiennej@upenn.edu&id=1422748452065263617" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/twitter/retweet/
```
- still gives `{"success":true,"posted":{"user":"User email not found"}}`

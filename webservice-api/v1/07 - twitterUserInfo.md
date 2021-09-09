**Twitter User Info**
----
  After twitter authorization complete.
  To get user name, display name and display image for the user from Twitter. 
 

* **URL**

  /twitter/userinfo

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`   

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"name":"ABC","screen_name":"nameABC","profile_image_url_https":"https:\/\/pbs.twimg.com\/profile_images\/116442460594752\/ila_PDvu_normal.jpg"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"User not found"}`

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

*  **Example URL**<br>


[https://sal.asc.upenn.edu/armt-hiv/v1/twitter/userinfo](https://sal.asc.upenn.edu/armt-hiv/v1/twitter/userinfo)


___________

### CURL POST REQUEST

```bash
curl -d "email=etiennej@upenn.edu" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/twitter/userinfo/
```

- this should work, returning:`{"name":"Etienne Jacquot","screen_name":"JacquotEtienne","profile_image_url_https":"https:\/\/pbs.twimg.com\/profile_images\/1022129819427860481\/ta4epKT4_normal.jpg"}`

You can confirm it's the real profile pic for my twitter account [https://twitter.com/JacquotEtienne](https://twitter.com/JacquotEtienne)! 

![](https://pbs.twimg.com/profile_images/1022129819427860481/ta4epKT4_normal.jpg)


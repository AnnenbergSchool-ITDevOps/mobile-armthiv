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


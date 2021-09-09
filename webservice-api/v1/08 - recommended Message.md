**Get Recommended Message**
----
  Get recommended message by date

* **URL**

  /recMsg

* **Method:**

  `POST`

*  **Params**

   **Optional:**

   `date=[string]` in YYYYMMDD<br />
   
*  **Description** <br />
Default is return today's recommended message. If 'date' is inputed, it will return the recommended message on 'date'  <br />
Since the database's messages generation is not finish yet, only the date between 20200601 to 20200610 have message for example,<br />. <br />
> (*THIS IS LEGACY INFO, NOT SURE ABOUT THE LATEST AVAILABLE TWEETS DATE BUT WE WANT NEAR DAILY?*)

[http://sal.asc.upenn.edu/armt-hiv/v1/recMsg/?date=20200604](http://sal.asc.upenn.edu/armt-hiv/v1/recMsg/?date=20200604)

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"success":true,"posted":"user updated"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"No User found"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"password incorrect"}`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/userinfo",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```


___________

### CURL POST REQUEST

```bash
curl -d "date=20200604" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/recMsg/
```

- this will return a long output for that date's tweets (you can just navigate in browser for [https://sal.asc.upenn.edu/armt-hiv/v1/recMsg/?date=20200604](https://sal.asc.upenn.edu/armt-hiv/v1/recMsg/?date=20200604))
  - our dev server does not have latest, so the following is blank (no error): [https://sal.asc.upenn.edu/armt-hiv/v1/recMsg/](https://sal.asc.upenn.edu/armt-hiv/v1/recMsg/))
**Teamlyzer API**
----
  Just replace xx in https://xx.teamlyzer.com with the country locator. **pt** for portuguese and **br** for brasilian data.

* **URL**

  api/rating/<int:company_id>

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `company_id=[integer]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{ "company_id": 67, "company_name": "CWI Software", "rating": 1.8 }`
 
* **Error Response:**

  * **Code:** 200  <br />
    **Content:** `{ "Error": "No company available for this ID" }`
    
  OR
  
  * **Code:** 404  NOT FOUND <br />


* **Sample Call:**

    api/rating/67
 

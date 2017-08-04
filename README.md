[![PyPI](https://img.shields.io/pypi/v/nine.svg?label=Version)]()

**Teamlyzer API**
=================
Just replace `xx` in `https://xx.teamlyzer.com` with the country locator. **pt** for portuguese and **br** for brazilian data.

Table of contents
=================

  * [Teamlyzer API](#teamlyzer-api)
  * [Table of contents](#table-of-contents)
  * [Authentication](#authentication)
  * [Usage](#usage)
    * [Get overall rating for a company](#get-overall-rating-for-a-company)
    * [Get detailed rating for a company](#get-detailed-rating-for-a-company)
    * [Get total of job reviews ordered by company total](#get-total-of-job-reviews-ordered-by-company-total)
    * [Get total of interview reviews ordered by company total](#get-total-of-interview-reviews-ordered-by-company-total)
    * [Get job reviews for a company](#get-job-reviews-for-a-company)
    * [Get interview reviews for a company](#get-interview-reviews-for-a-company)
  * [CSS](#css)

Authentication
=================

The access and use are free. To prevent the server overloaded please request user and pass.

`curl -u user:pass -i https://xx.teamlyzer.com/api/endpoint`

Usage
=====

Get overall rating for a company
-----

* **URL**

  `api/rating/<int:company_id>`

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `company_id=[integer]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{ "company_id": 67, "company_name": "CWI Software", "rating": 1.8, "url": "https://br.teamlyzer.com/companies/cwi-software/interview-reviews" }`
    
    **Rating metric:** x/5
    
    **Style:** `{% if rating < 1.5 %} .f_rating {% elif rating < 2.0 %} .e_rating {% elif rating < 2.5 %} .d_rating {% elif rating < 3.0 %} .c_rating {% elif rating < 3.5 %} .b_rating {% elif rating <= 4.0 %} .a_rating {% elif rating <= 5.0 %} .aa_rating {% endif %}`
 
* **Error Response:**

  * **Code:** 200  <br />
    **Content:** `{ "Error": "No company available for this ID" }`
    
  OR
  
  * **Code:** 404  NOT FOUND <br />


* **Sample Call:**

    `api/rating/67`
 
 
Get detailed rating for a company
-----

* **URL**

  `api/detailed_rating/<int:company_id>`

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `company_id=[integer]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{ "career opportunity": "75.0", "company_id": 67, "company_name": "CWI Software", "interview difficult": 20.0, "management quality": "75.0", "recognition and reward": "50.0", "salary": "25.0", "work life balance": "50.0", "url": "https://br.teamlyzer.com/companies/cwi-software/interview-reviews" }`
    
    **Rating metric:** x/100 
 
* **Error Response:**

  * **Code:** 200  <br />
    **Content:** `{ "Error": "No company available for this ID" }`
    
     OR
  
  * **Code:** 404  NOT FOUND <br />


* **Sample Call:**

    `api/detailed_rating/67`

Get total of job reviews ordered by company total
-----

* **URL**

  `api/total-job-reviews`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `[ { "company_id": 67, "company_name": "CWI Software", "company_total_reviews": 1, "url": "https://br.teamlyzer.com/companies/cwi-software/interview-reviews" } ]`
 
* **Error Response:**
  
  * **Code:** 404  NOT FOUND <br />

* **Sample Call:**

    `api/total-interview-reviews`


Get total of interview reviews ordered by company total
-----

* **URL**

  `api/total-interview-reviews`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `[ { "company_id": 67, "company_name": "CWI Software", "company_total_reviews": 1, "url": "https://br.teamlyzer.com/companies/cwi-software/interview-reviews" } ]`
 
* **Error Response:**
  
  * **Code:** 404  NOT FOUND <br />

* **Sample Call:**

    `api/total-interview-reviews`
 
 
Get job reviews for a company
-----

* **URL**

  `api/job-reviews/<int:company_id>`

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `company_id=[integer]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `[ { "company": "CWI Software", "company_id": 67, "industry": "Software house & Internet", "rating": 2.6, "review_title": "Boa empresa para se come\u00e7ar", "size": "501-1,000", "tags": { "0": "javascript", "1": "c", "2": "java" }, "views": "110", "votes": 0, "url": "https://br.teamlyzer.com/companies/cwi-software/job-reviews" } ]`
    
    **Rating metric:** x/5 
    
    **Style:** `{% if rating < 1.5 %} .f_rating {% elif rating < 2.0 %} .e_rating {% elif rating < 2.5 %} .d_rating {% elif rating < 3.0 %} .c_rating {% elif rating < 3.5 %} .b_rating {% elif rating <= 4.0 %} .a_rating {% elif rating <= 5.0 %} .aa_rating {% endif %}`
 
* **Error Response:**

  * **Code:** 200  <br />
    **Content:** `{ "Error": "No company available for this ID" }`
    
  OR
  
  * **Code:** 404  NOT FOUND <br />


* **Sample Call:**

    `api/job-reviews/67`


 Get interview reviews for a company
-----

* **URL**

  `api/interview-reviews/<int:company_id>`

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `company_id=[integer]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `[ { "company": "CWI Software", "company_id": 67, "industry": "Software house & Internet", "rating": 1.0, "review_title": "Um bom estilo de entrevista", "size": "501-1,000", "views": "42", "votes": 0, "url": "https://br.teamlyzer.com/companies/cwi-software/interview-reviews" } ]`
    
    **Rating metric:** x/5
    
    **Style:** `{% if rating < 1.5 %} .aa_rating {% elif rating < 2.0 %} .a_rating {% elif rating < 2.5 %} .b_rating {% elif rating < 3.0 %} .c_rating {% elif rating < 3.5 %} .d_rating {% elif rating <= 4.0 %} .e_rating {% elif rating <= 5.0 %} .f_rating {% endif %}`
     
* **Error Response:**

  * **Code:** 200  <br />
    **Content:** `{ "Error": "No company available for this ID" }`
    
  OR
  
  * **Code:** 404  NOT FOUND <br />


* **Sample Call:**

    `api/interview-reviews/67`
    

CSS
==========

 `.aa_rating{
	color:white;
	background-color: #257C00 !important;
	font-size: 25px;
	padding: 2px 5px;
	font-weight: bold;
	-webkit-border-radius: 3px !important;
	-moz-border-radius: 3px !important;
	border-radius: 3px !important;
	opacity: 0.8;
}`

`.a_rating{
	color:white;
	background-color: #3F7E00 !important;
	font-size: 25px;
	padding: 2px 5px;
	font-weight: bold;
	-webkit-border-radius: 3px !important;
	-moz-border-radius: 3px !important;
	border-radius: 3px !important;
	opacity: 0.8;
}`

`.b_rating{
	color:white;
	background-color: #5BA829 !important;
	font-size: 25px;
	padding: 2px 5px;
	font-weight: bold;
	-webkit-border-radius: 3px !important;
	-moz-border-radius: 3px !important;
	border-radius: 3px !important;
	opacity: 0.8;
}`

`.c_rating{
	color:white;
	background-color: #9ACD32 !important;
	font-size: 25px;
	padding: 2px 5px;
	font-weight: bold;
	-webkit-border-radius: 3px !important;
	-moz-border-radius: 3px !important;
	border-radius: 3px !important;
	opacity: 0.8;
}`

`.d_rating{
	color:white;
	background-color: #EDD614 !important;
	font-size: 25px;
	padding: 2px 5px;
	font-weight: bold;
	-webkit-border-radius: 3px !important;
	-moz-border-radius: 3px !important;
	border-radius: 3px !important;
	opacity: 0.8;
}`

`.e_rating{
	color:white;
	background-color: #FFBA00 !important;
	font-size: 25px;
	padding: 2px 5px;
	font-weight: bold;
	-webkit-border-radius: 3px !important;
	-moz-border-radius: 3px !important;
	border-radius: 3px !important;
	opacity: 0.8;
}`

`.f_rating{
	color:white;
	background-color: #FF7800 !important;
	font-size: 25px;
	padding: 2px 5px;
	font-weight: bold;
	-webkit-border-radius: 3px !important;
	-moz-border-radius: 3px !important;
	border-radius: 3px !important;
	opacity: 0.8;
}`

# Final Project 4 Kelompok 4 Aplikasi Toko Belanja
Ini adalah project keempat dari program MSIB di Hacktiv8. Project kali ini adalah membuat sebuah aplikasi berjudul "Toko Belanja" dimana terdapat seorang admin yang berwenang melakukan perintah CRUD pada category dan juga product dan customer-customer yang bisa melakukan top up untuk membeli product dan juga bisa melihat transaksi pembeliannya.


### Base Local URL   : `http://192.34.60.90:8080`

### End Points
**USER**
* POST (Register) :
    * Untuk menambahkan user customer baru dapat dengan menggunakan url :
    
    * Kemudian gunakan json berikut untuk membuat datanya:
        ```json
            {
                "full_name" : "Ali",
	            "email" : "ali@gmail.com",
	            "password" : "ali123"
            }
        ```
    * Jika berhasil maka akan muncul response seperti berikut:
        ```json
            {
                "data": {
		        "id": 2,
		        "CreatedAt": "2022-12-06T16:36:16.961+07:00",
		        "UpdatedAt": "0001-01-01T00:00:00Z",
		        "fullname": "Ali",
		        "email": "ali@gmail.com",
		        "password": "$2a$08$QM0aJg/UhLP9xkjFaiDe/OQfiEK9IPMo882rajDIlL0VbjGHJKE.K",
		        "balance": 0
            }
            }
        ```
* POST (Login) :
    * Untuk login user customer dapat dengan menggunakan url :
    * Akun admin telah terdaftar di database, sehingga tidak perlu melakukan register. Untuk login, gunakan username dan password berikut:
 ```json
            {
                "email" : "admin@admin.com",
	            "password" : "password123"
            }
```
* Jika berhasil maka akan muncul response seperti berikut:
    ```json
            {
                "data": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJpc3MiOiJoYWNrdGl2OC1maW5hbDMiLCJleHAiOjE2NzA0MDcxMDJ9.ktbiKmEpxkio2oIQ-Q2ckGUXJX-Uw-j6TaWkGBkxEQo"
            }

* Patch (Top Up) :
    * Untuk melakukan top up balance user customer dapat dengan menggunakan url :
    *berikan token pada headers
    * Kemudian gunakan json berikut untuk membuat datanya:

    ```
            {
                "balance" : 500
            }
    ```
    * Jika berhasil maka akan muncul response seperti berikut:

    ```
            {
               "data": "Balance updated"
            }
     ```
**CATEGORIES**
* GET :
    * Untuk menampilkan semua data categories dapat dengan menggunakan url :
    `http://localhost:8080/categories` dengan method **GET**
    * Untuk dapat mengakses endpointnya dibutuhkan autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        [
            {
                "id": 1,
                "type": "Drinks",
                "sold_product_amount": 0,
                "created_at": "2022-12-07T08:08:19Z",
                "updated_at": "2022-12-07T08:09:56Z",
                "products": [
                    {
                        "id": 2,
                        "CreatedAt": "2022-12-07T08:33:10Z",
                        "UpdatedAt": "2022-12-07T08:33:10Z",
                        "title": "Pocari Sweat",
                        "price": 8500,
                        "stock": 25
                    },
                    {
                        "id": 4,
                        "CreatedAt": "2022-12-07T08:36:15Z",
                        "UpdatedAt": "2022-12-07T08:36:15Z",
                        "title": "Yakult",
                        "price": 9000,
                        "stock": 55
                    },
                    {
                        "id": 9,
                        "CreatedAt": "2022-12-07T11:33:43Z",
                        "UpdatedAt": "2022-12-07T11:33:43Z",
                        "title": "NU",
                        "price": 5000,
                        "stock": 5
                    }
                ]
            },
            {
                "id": 2,
                "type": "Foods",
                "sold_product_amount": 0,
                "created_at": "2022-12-07T08:34:55Z",
                "updated_at": "2022-12-07T08:34:55Z",
                "products": [
                    {
                        "id": 3,
                        "CreatedAt": "2022-12-07T08:35:29Z",
                        "UpdatedAt": "2022-12-07T08:35:29Z",
                        "title": "Taro rasa Potato BBQ",
                        "price": 8000,
                        "stock": 15
                    },
                    {
                        "id": 10,
                        "CreatedAt": "2022-12-07T11:34:25Z",
                        "UpdatedAt": "2022-12-07T11:34:25Z",
                        "title": "Cheetos",
                        "price": 7000,
                        "stock": 15
                    }
                ]
            }
        ]
        ```

* POST :
    * Untuk membuat data categories baru dapat dengan menggunakan url :
    `http://localhost:8080/categories` dengan method **POST**
    * Kemudian gunakan json berikut untuk membuat datanya:
        ```json
        {
            "type" : "Tools"
        }
        ```
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
            "id": 6,
            "type": "Tools",
            "sold_product_amount": 0,
            "created_at": "2022-12-08T20:05:25.038+07:00"
        }
        ```

* PATCH :
    * Untuk mengedit data categories dengan id 6 dapat dengan menggunakan url :
    `http://localhost:8080/categories/6` dengan method **PATCH**
    * Kemudian gunakan json berikut untuk mengedit datanya:
        ```json
        {
            "type" : "Tools Updated"
        }
        ```
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
            "id": 6,
            "type": "Tools Updated",
            "sold_product_amount": 0,
            "updated_at": "2022-12-08T13:06:42Z"
        }
        ```
* DELETE :
    * Untuk menghapus data categories dengan id 6 dapat dengan menggunakan url :
    `http://localhost:8080/categories/6` dengan method **DELETE**
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
            "message": "category has been successfully deleted"
        }
        ```


**PRODUCT**
<br> NOTES : Selain dari perintah **'GET'**, semua perintah lain hanya bisa diakses oleh admin. Jika customer melakukan perintah 'POST','DEL','PUT', maka akses akan ditolak dengan response seperti ini :
   <br> ```
    {
        "error": "You aren't allowed to do this! You are not Admin!""
        }
        ```
* GET :
    * Untuk menampilkan semua product dapat dengan menggunakan url :
    `http://localhost:8080/products` dengan method **GET**
    * Output response yang dihasilkan adalah :
        ```json
    [
        {
            "id": 1,
            "CreatedAt": "2022-12-05T03:30:11.716Z",
            "UpdatedAt": "2022-12-05T03:30:11.716Z",
            "title": "tote bag",
            "stock": 5,
            "price": 25000,
            "category_id": 1
        },
        {
            "id": 2,
            "CreatedAt": "2022-12-05T03:30:57.85Z",
            "UpdatedAt": "2022-12-05T03:30:57.85Z",
            "title": "sling bag",
            "stock": 5,
            "price": 35000,
            "category_id": 1
        },

            ]
        ```

* POST :
    * Untuk menambahkan product baru dapat dengan menggunakan url :
    `http://localhost:8080/products` dengan method **POST**
    * Kemudian gunakan json berikut untuk membuat datanya:
        ```json
            {
                "title":"fanta",
                "stock":20,
                "price":5000,
                "category_id":2

            }
        ```
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
            "id": 5,
            "title": "fanta",
            "stock": 20,
            "price": 5000,
            "category_id": 2,
            "created_at": "2023-06-22T11:11:05.712+07:00"
            }
        ```

* PUT :
    * Misalnya untuk mengedit data product dengan id 7 dapat dengan menggunakan url :
    `http://localhost:8080/products/7` dengan method **PUT**
    * Kemudian gunakan json berikut untuk mengedit datanya:
        ```json
        {
            "title":"sprite",
            "stock":15,
            "price":6000,
            "category_id":2
        }
        ```
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
            "id": 5,
            "title": "sprite",
            "stock": 15,
            "price": 6000,
            "category_id": 2,
            "created_at": "2023-06-22T04:11:05.712Z",
            "updated_at": "2023-06-22T11:14:47.31+07:00"
        }
        ```
* DELETE :
    * Misalnya untuk menghapus product dengan id 7 dapat dengan menggunakan url :
    `http://localhost:8080/products/7` dengan method **DELETE**
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
        "message": "Product has been successfully deleted"
        }
        ```

**TRANSACTION HISTORY**
* GET :
    * Untuk menampilkan semua data transaction history dengan role admin dapat dengan menggunakan url :
    `http://localhost:8080/transactions/user-transactions` dengan method **GET**
    * Untuk dapat mengakses endpointnya dibutuhkan autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
	    "transaction_history": [
		{
		    "id": 3,
		    "product_id": 2,
		    "user_id": 1,
		    "quantity": 3,
		    "total_price": 0,
		    "product": {
			"id": 2,
			"title": "Pocari Sweat",
			"price": 8500,
			"stock": 8,
			"category_id": 1,
			"created_at": "2022-12-07T08:33:10Z",
			"updated_at": "2022-12-10T05:32:06Z"
		    },
		    "user": {
			"id": 1,
			"fullname": "Admin",
			"email": "admin@admin.com",
			"balance": 200,
			"created_at": "2022-12-06T09:32:14Z",
			"updated_at": "2022-12-06T09:35:46Z"
			    }
		}
		]
          }
        
        ```
	
* GET :
    * Untuk menampilkan semua data transaction history dengan role admin dapat dengan menggunakan url :
    `http://localhost:8080/transactions/user-transactions` dengan method **GET**
    * Untuk dapat mengakses endpointnya dibutuhkan autorisasi token yang didapatkan dari response endpoint user/login. (**Hanya bisa diakses oleh user dengan role ADMIN**)
    * Output response yang dihasilkan adalah :
        ```json
        {
	    "transaction_history": [
		{
		    "id": 3,
		    "product_id": 2,
		    "user_id": 1,
		    "quantity": 3,
		    "total_price": 0,
		    "product": {
			"id": 2,
			"title": "Pocari Sweat",
			"price": 8500,
			"stock": 8,
			"category_id": 1,
			"created_at": "2022-12-07T08:33:10Z",
			"updated_at": "2022-12-10T05:32:06Z"
		    }
		}
		]
          }
        
        ```

* POST :
    * Untuk membuat data transaction baru dapat dengan menggunakan url :
    `http://localhost:8080/transactions` dengan method **POST**
    * Kemudian gunakan json berikut untuk membuat datanya:
        ```json
	    {
	        "product_id" : 6,
	        "quantity" : 1
		}
        ```
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login.  
    * Output response yang dihasilkan adalah :
    
        ```json
 {
            "message": "Transaction Success",
            "transaction_bill": [
        {
            "total_price": 5000,
            "quantity": 1,
            "product_title": "fanta"
        }
    ]
}
        ```

 
* DELETE :
    * Untuk menghapus data transaction dengan id 6 dapat dengan menggunakan url :
    `http://localhost:8080/transactions/6` dengan method **DELETE**
    * Untuk akses endpointnya dibutuhkan request autorisasi token yang didapatkan dari response endpoint user/login.  
    * Output response yang dihasilkan adalah :
        ```json
        {
            "message": "transactions has been successfully deleted"
        }
        ```


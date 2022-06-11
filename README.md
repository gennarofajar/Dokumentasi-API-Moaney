# :zap: **『Kelompok 4』- Dokumentasi API Moaney** :zap:

| Nama                      | NRP        |
|---------------------------|------------|
| Muhammad Firdho Kustiawan | 5027201005 |
| M. Fernando N Sibarani    | 5027201015 |
| Gennaro Fajar Mennde      | 5027201061 | 
<br/>

| Metode   | End Point                                            | Dokumentasi | Deskripsi                                |
|----------|------------------------------------------------------|-------------|------------------------------------------|
| POST     |[Register](#Register) <br/> `http://e-moaney.herokuapp.com/public/api/register`   |-------------|------------------------------------------|
| POST     |[Login](#Login) <br/> `http://e-moaney.herokuapp.com/public/api/login`            |-------------|------------------------------------------|
| GET      |ip_ewallet/api/profile                  |-------------|------------------------------------------|
| PUT      |ip_ewallet/api/profile/{id_user}        |-------------|------------------------------------------|
| POST     |ip_ewallet/api/transaksi                |-------------|------------------------------------------|

<br/>

## :large_blue_circle: **Register** :large_blue_circle: 
### **Method** : `POST` 
### **URL**    : `http://e-moaney.herokuapp.com/public/api/register`
### **Properties**
- **Params** : -
- **Authorization** : -
- **Body** : <br/> 
    ◢ x-www-form-urlencoded
    | Key      | Value           | 
    |----------|-----------------|
    | nama     | Laila           |
    | email    | laila@gmail.com |
    | password | laila1234       | 
    
    ◢ JSON
    ```json
    {  
        "nama": "Laila",
        "email":"laila@gmail.com",
        "password": "laila1234"
    }
    ```
### **HTTP Responses**
- **200** <br/> Apabila pendaftaran berhasil
    ```json
    {
        "status": 200,
        "message": "Pendaftaran Berhasil",
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjgifQ.CZii4GKUtqTgvt_nKXBZQ5mhXzVxPfKJSrVkSudTf4Y"
    }
    ```
- **400** <br/> Apabila email yang didaftarkan sudah ada
    ```json
    {
        "status": 400,
        "message": "Email sudah terdaftar"
    }
    ```
- **500**
    ```json
    {
        "status": 500,
        "message": "Server Error"
    }
    ```

<br/>

## :large_blue_circle: **Login** :large_blue_circle: 
### **Method** : `POST` 
### **URL**    : `http://e-moaney.herokuapp.com/public/api/login`
### **Properties**
- **Params** : -
- **Authorization** : -
- **Body** : <br/> 
    ◢ x-www-form-urlencoded
    | Key      | Value           | 
    |----------|-----------------|
    | email    | laila@gmail.com |
    | password | laila1234       | 
    
    ◢ JSON
    ```json
    {  
        "email":"laila@gmail.com",
        "password": "laila1234"
    }
    ```
### **HTTP Responses**
- **200** <br/> Apabila login berhasil
    ```json
    {
        "status": 200,
        "message": "Login Berhasil",
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjgifQ.CZii4GKUtqTgvt_nKXBZQ5mhXzVxPfKJSrVkSudTf4Y"
    }
    ```
- **400** <br/> Apabila email atau password belum diisi
    ```json
    {
        "status": 400,
        "message": "Email dan Password harus diisi"
    }
    ```
- **500**
    ```json
    {
        "status": 500,
        "message": "Server Error"
    }
    ```

<br/>

## :large_blue_circle: **Profile** :large_blue_circle: 
### **Method** : `GET` 
### **URL**    : `http://e-moaney.herokuapp.com/public/api/profile`
### **Properties**
- **Params** : -
- **Authorization** : <br/>
    Bearer Token
    ```js
    eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjgifQ.CZii4GKUtqTgvt_nKXBZQ5mhXzVxPfKJSrVkSudTf4Y
    ```
- **Body** : -

### **HTTP Responses**
- **200** <br/> Apabila berhasil
    ```json
    {
        "id": "8",
        "nama": "Laila",
        "email": "laila@gmail.com",
        "saldo": "0",
        "nomor wallet": "751487997112"
    }
    ```
- **400** <br/> Apabila tidak ada token
    ```json
    {
        "status": 400,
        "message": "Silahkan masukkan token"
    }
    ```
- **500**
    ```json
    {
        "status": 500,
        "message": "Server Error"
    }
    ```

<br/>

## :large_blue_circle: **Top Up** :large_blue_circle: 
### **Method** : `PUT` 
### **URL**    : `http://e-moaney.herokuapp.com/public/api/topup`
### **Properties**
- **Params** : -
- **Authorization** : <br/>
    Bearer Token
    ```js
    eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjgifQ.CZii4GKUtqTgvt_nKXBZQ5mhXzVxPfKJSrVkSudTf4Y
    ```
- **Body** : <br/>
    ◢ x-www-form-urlencoded
    | Key      | Value           | 
    |----------|-----------------|
    | jumlah   | 100000          |
    
    ◢ JSON **(Tidak Bisa)**

### **HTTP Responses**
- **200** <br/> Apabila berhasil
    ```json
    {
        "status": 200,
        "message": "Top up berhasil"
    }
    ```
- **400** <br/> Apabila tidak ada token
    ```json
    {
        "status": 400,
        "message": "Silahkan masukkan token"
    }
    ```
    Apabila tidak memasukkan jumlah
    ```json
    {
        "status": 400,
        "message": "jumlah harus lebih dari 0"
    }
    ```

- **500**
    ```json
    {
        "status": 500,
        "message": "Server Error"
    }
    ```

<br/>

## :large_blue_circle: **Transaksi** :large_blue_circle: 
### **Method** : `POST` 
### **URL**    : `http://e-moaney.herokuapp.com/public/api/transaksi`
### **Properties**
- **Params** : -
- **Authorization** : <br/>
    Bearer Token
    ```js
    eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjgifQ.CZii4GKUtqTgvt_nKXBZQ5mhXzVxPfKJSrVkSudTf4Y
    ```
- **Body** : <br/>
    ◢ x-www-form-urlencoded
    | Key                      | Value           | 
    |--------------------------|-----------------|
    | jumlah                   | 100000          |
    | nomor-wallet-client      | 751487997112    |
    | nomor-wallet-ecommerce   | 722710603682    |
    | referensi                | ---    |
    
    ◢ JSON **(Tidak Bisa)**

### **HTTP Responses**
- **200** <br/> Apabila berhasil
    ```json
    {
        "status": 200,
        "message": "Permintaan pembayaran berhasil"
    }
    ```
- **400** <br/> Apabila tidak ada token
    ```json
    {
        "status": 400,
        "message": "..."
    }
    ```
- **500**
    ```json
    {
        "status": 500,
        "message": "Server Error"
    }
    ```

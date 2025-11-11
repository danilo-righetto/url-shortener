# Principais Endpoints

Os principais endpoints são da aplicação são: o **encurtamento da URL** e **redirecionamento da URL**.

## Endpoint de Encurtamento da URL

**Request**:

```sh
Método: POST
Endpoint: api/v1/shorten
Body: {"url": "www.example.com..."}
```

**Response**:
```sh
Status Code: 201 (created)
{"short_url": "bit.ly/zn9e10A"}
```

---

## Endpoint de Redirecionamento da URL

**Request**:

```sh
Método: GET
Endpoint: "bit.ly/zn9e10A"
```

**Response**:
```sh
Status Code: 301/302 (redirect)
Header: 
    Location: "www.example.com/..."
```

---
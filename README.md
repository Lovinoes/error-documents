# Error Documents
This repository contains a collection of error documents

### Preview
https://error-docs.lovinoes.de

<details>
<summary><em><b>Click here to expand</b></em></summary>
<br>


**400 Bad Request**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/85f9bfcd-0c09-47e4-8a1c-a529280766d5" />

**401 Authorization Required**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c28e8018-27f0-4801-8c7a-74f479c70008" />

**403 Forbidden**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b5146408-ef82-4b53-87ab-863404797a5f" />

**404 Page Not Found**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0294847f-7250-4e94-8b1b-4bccd3f1f6f1" />

**405 Method Not Allowed**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c6144609-3ce4-4b0b-9010-8e237bb9d10d" />

**406 Not Acceptable**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d17541bb-5d92-4e7d-9eeb-66ac7a94d509" />

**407 Proxy Authentication Required**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d739b7f4-71be-44a3-9626-e99dcf9cbcb1" />

**412 Precondition Failed**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/348af4bf-4062-4d30-b7e7-8f3d8a93d79c" />

**414 Request-URI Too Long**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/77fad358-895f-4061-94e9-874256b57e2f" />

**415 Unsupported Media Type**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c304e545-f982-48fe-b0c5-fcb97147081b" />

**500 Internal Server Error**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2193d6ff-8941-4af7-96de-09273fc3354a" />

**501 Not Implemented**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e386049e-7b1f-4202-943c-8f994bd843e9" />

**502 Bad Gateway**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e13f23b3-f5d2-4fd4-8ef4-f617c9e8257f" />

**503 Service Unavailable**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4ac75037-2139-4bfe-86c0-66c0bac72a20" />


</details>

---

### Formats

| Folder | Use |
| --- | --- |
| `standalone/` | One self-contained page per status code |
| `plesk/` | Same pages, named for Plesk's error document slots |
| `nginx-ssi/` | **One** page for every code, filled in by nginx at request time |

### nginx (SSI)

`nginx-ssi/error.html` replaces all fourteen standalone pages with a single
file. nginx substitutes the status code and matching message via Server Side
Includes, so there is one file to restyle instead of fourteen.

Copy it into your web root and point every code at it:

```nginx
error_page 400 401 403 404 405 406 407 412 414 415 429 500 501 502 503 /error.html;

location = /error.html {
    ssi              on;
    ssi_value_length 1024;
    internal;
}
```

`internal` keeps it from being fetched directly as a normal URL. The original
status code is preserved in the response — nginx only replaces the body.

`ssi_value_length` is required: it defaults to 256 bytes and the 500 message is
326, so without it that one code renders with an empty message.

It uses the same colours, fonts and buttons as [lovinoes.de](https://lovinoes.de),
and expects `Chakra Petch` at `/assets/fonts/`; without those it falls back to
the system sans-serif, which is why the preview above looks different.

---

### License
This repository is licensed under the MIT License. See the [LICENSE](https://github.com/Lovinoes/error-documents/blob/main/LICENSE) file for more information.

### Contact
If you have any questions, feel free to contact me at lovinoes@lovinoes.de

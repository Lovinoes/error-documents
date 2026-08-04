# Error Documents

Dark, minimal HTTP error pages for nginx, Apache, Plesk and friends — styled to
match [lovinoes.de](https://lovinoes.de).

**Preview** → https://error-docs.lovinoes.de

<details>
<summary><em><b>Screenshots</b></em></summary>
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

**408 Request Timeout**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/628c9024-c85c-47cf-98f3-46a867a445bd" />

**412 Precondition Failed**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/348af4bf-4062-4d30-b7e7-8f3d8a93d79c" />

**413 Request Entity Too Large**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e6657ad1-6f41-4431-b99f-628991fc89f8" />

**414 Request-URI Too Long**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/77fad358-895f-4061-94e9-874256b57e2f" />

**415 Unsupported Media Type**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c304e545-f982-48fe-b0c5-fcb97147081b" />

**429 Too Many Requests**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/168c0b4d-3d8d-4f22-a705-28d8f7ed26ac" />

**431 Request Header Fields Too Large**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/60f5fefa-fe36-44bc-a426-1adcc83d16b4" />

**500 Internal Server Error**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2193d6ff-8941-4af7-96de-09273fc3354a" />

**501 Not Implemented**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e386049e-7b1f-4202-943c-8f994bd843e9" />

**502 Bad Gateway**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e13f23b3-f5d2-4fd4-8ef4-f617c9e8257f" />

**503 Service Unavailable**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4ac75037-2139-4bfe-86c0-66c0bac72a20" />

**504 Gateway Timeout**
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/66e514f6-aacf-4cde-8f5c-2fad51cf9b1d" />

</details>

## Formats

| Folder | What you get |
| --- | --- |
| `standalone/` | One page per status code |
| `plesk/` | The same pages, named for Plesk's error document slots |
| `nginx-ssi/` | A single page covering every code, filled in by nginx |

Covered: `400` `401` `403` `404` `405` `406` `407` `408` `412` `413` `414` `415`
`429` `431` `500` `501` `502` `503` `504`

## nginx (SSI)

One file instead of nineteen. Copy `nginx-ssi/error.html` into your web root:

```nginx
error_page 400 401 403 404 405 406 407 408 412 413 414 415 429 431
           500 501 502 503 504 /error.html;

location = /error.html {
    ssi              on;
    ssi_value_length 1024;
    internal;
}
```

`ssi_value_length` is required — the 256-byte default truncates the 500 message.
`internal` keeps it from being fetched as a normal URL. The status code is
preserved; nginx only swaps the body.

## Fonts

Chakra Petch loads from [Bunny Fonts](https://fonts.bunny.net). EU-hosted with no
cookies, no tracking whatsoever.

---

MIT licensed, see [LICENSE](LICENSE) · Questions: lovinoes@lovinoes.de

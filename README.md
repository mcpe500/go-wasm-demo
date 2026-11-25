# go-wasm-demo

Demo backend Go untuk preset **Go (WASM)** di Strataflow.

## Kontrak

Satu-satunya yang platform butuh dari repo ini:

```go
func Handle(w http.ResponseWriter, r *http.Request)
```

(di package `main`, plus `func main() {}` kosong). Tidak ada file khusus platform,
tidak ada import platform — Go biasa.

## Endpoint

| Route | Method | Perilaku |
| :-- | :-- | :-- |
| `/` | GET | info service (JSON) |
| `/api/users` | POST | terima JSON, balas 201 + id |
| `/env` | GET | baca env project via `envGet("GREETING")` |
| `/big` | GET | alokasi 2 MB — untuk uji cap memori (trap di tier 1 MB) |
| `/loop` | GET | loop tak hingga — untuk uji timeout 10 s |

## Deploy

1. Wizard → preset **Go (WASM)** → tier memori 2 MB (default).
2. Sambungkan repo ini.
3. Endpoint `<slug>.<domain>/` hidup. Coba `GET /`, `POST /api/users`.

<div align="center">
  <h1>🌴 api kbbi jalur nyawit (gratis)</h1>
  <p>buat lu pada yang miskin resource nyari api butuh wordle atau sambung kata</p>
</div>

---

berhubung api kbbi di luar sana pada ampas, gampang meledak, atau isinya cuma hasil scraping gajelas, gua buatin yg beneran jalan. 

api ini **gratis 100%, ngebut parah (ditaro di node cloudflare langsung), dan gada limit api key yang cringe.** databasenya 112k+ full kata baku sama serapan.

pake aja sesuka lu buat game roblox luau lu atau bot discord. server gua kuat nampung.

---

## ⚡ cara makenya (kalo lu ngerti baca)
tembak *GET request* ke url ini:

```http
GET https://kbbi-api.ruell.workers.dev/api/lookup/kata-yg-lu-cek
```

---

## 📦 json response (jangan nanya mulu)

### ✅ misal kata nya valid (`/api/lookup/sawit`)
kalo ada di kamus (dan direstui pak prabowo nanam energi alternatif), `exists` bakal `true`:
```json
{
  "exists": true,
  "data": {
    "entri": [
      {
        "nama": "sawit",
        "makna": [
          "palem yang buahnya dapat diolah menjadi minyak; kelapa sawit"
        ]
      }
    ]
  }
}
```

### ❌ misal kata nya ngaco (`/api/lookup/ndasmu`)
kalo typo atau emang kaga baku:
```json
{
  "exists": false
}
```

---

## 💻 copas code (tinggal tempel)

### 1. buat dev roblox luau (kalo lu main studio)
```lua
local HttpService = game:GetService("HttpService")
local kata = "makan"
local url = "https://kbbi-api.ruell.workers.dev/api/lookup/" .. string.lower(kata)

local obj, response = pcall(function()
    return HttpService:GetAsync(url)
end)

if obj then
    local hasil = HttpService:JSONDecode(response)
    if hasil.exists then
        print("baku cuy, lanjut")
    else
        print("kaga valid dongo")
    end
end
```

### 2. javascript (fetch)
```javascript
const kata_dicari = "pertanian";
const res = await fetch(`https://kbbi-api.ruell.workers.dev/api/lookup/${kata_dicari}`);
const json = await res.json();

if (json.exists) {
    console.log("valid");
} else {
    console.log("baca kamus makanya wkwk");
}
```

### 3. curl di terminal (kalo lu si paling hacker distro linux)
```bash
curl -s https://kbbi-api.ruell.workers.dev/api/lookup/sawit
```

---
*udah ah, gausah banyak bacot mending gas koding aja.*

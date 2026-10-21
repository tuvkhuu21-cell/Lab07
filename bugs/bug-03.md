# BUG-03 — Буруу JSON илгээхэд HTTP 200 буцааж байна

## Орчин
- Апп: Уншлагын жагсаалт v2.0
- OS: Windows + Ubuntu (WSL)
- Node.js: v22.22.1
- Хэрэгсэл: curl
- Огноо: 2026-10-21
- Tour: Saboteur Tour

## Урьдчилсан нөхцөл
Апп `http://localhost:3000` хаягт ажиллаж байна.

## Дахин үүсгэх алхмууд
1. Ubuntu Terminal нээнэ.
2. Дараах командыг ажиллуулна:

```bash
curl -i -X POST http://localhost:3000/api/books \
  -H "Content-Type: application/json" \
  --data 'invalid json'
```

3. Серверийн HTTP статус болон хариуг шалгана.

## Хүлээгдсэн үр дүн
Хүсэлтийн өгөгдөл хүчинтэй JSON биш тул сервер
`HTTP 400 Bad Request` буцаах ёстой.

## Бодит үр дүн
Сервер дараах хариуг буцаасан:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"result":"OK"}
```

## Severity
Major — Сервер буруу хүсэлтийг амжилттай гэж
мэдээлж байгаа нь API ашиглаж буй системүүдэд
төөрөгдөл үүсгэх эрсдэлтэй.

## Evidence
[BUG-03 — HTTP хариу](../evidence/bug-03-curl.txt)

## Session
`session-report.md` — 17:24.

Concepts:
# XFF (X-Forwarded-For)
เป็นหนึ่งในวิธีการ bypass rate limit
เอาไว้ใช้สำหรับเปลี่ยน IP ของผู้ส่ง

ข้อนี้มีไฟล์ Passwords มาให้ ให้ใช้เมลที่กำหนดมาแล้วลอง Password แต่ละอัน แต่ทุกครั้งที่ใส่ Password จะถูก Rate Limit จึงต้องใช้ XFF มาช่วย

ไอเดียวิธีทำแบบโง่ๆคือ
1. ใส่พาสเวิร์ด
2. กดส่งและใส่ XFF Header โดยใช้ BurpSuite (เขียนว่า X-Forwarded-For: 8.8.8.8)
3. ทำซ้ำจนครบ

แต่ไฟล์มันมี Passwords ตั้งเยอะ ดังนั้นเราจะมาทำให้มันส่งเป็น Automation กัน เราจะใช้ tool ของ linux ชื่อ ffuf คือโปรแกรมการ fuzzing 
# fuzzing 
คือการทดสอบข้อมูลโดยส่งข้อมูลแบบสุ่มหลายๆ โดยข้อมูลอันนี้จะเป็น passwords นั่นเอง

payload จะหน้าตาประมาณนี้
<img width="454" height="75" alt="image" src="https://github.com/user-attachments/assets/f26f4b56-2550-4734-bc10-069c617f372b" />
{"email": "ctf-player@picoctf.org", "password": "test"}

ถ้าใช้ curl ส่งก็จะเป็น

`
curl -i http://amiable-citadel.picoctf.net:57852/login \
> -X POST \
> -H "Content-Type:application/json" \
> -H "X-Forwarded-For:127.0.0.1" \
> -d '{"email": "ctf-player@picoctf.org", "password": "test"}'
`

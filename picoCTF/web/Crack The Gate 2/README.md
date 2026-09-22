Concepts:
# XFF (X-Forwarded-For)
เป็นหนึ่งในวิธีการ bypass rate limit
เอาไว้ใช้สำหรับเปลี่ยน IP ของผู้ส่ง

ข้อนี้มีไฟล์ Passwords มาให้ ให้ใช้เมลที่กำหนดมาแล้วลอง Password แต่ละอัน แต่ทุกครั้งที่ใส่ Password จะถูก Rate Limit จึงต้องใช้ XFF มาช่วย

ไอเดียวิธีทำแบบโง่ๆคือ
1. ใส่พาสเวิร์ด
2. กดส่งและใส่ XFF Header โดยใช้ BurpSuite (เขียนว่า X-Forwarded-For: 8.8.8.8)
3. ทำซ้ำจนครบ

แต่ไฟล์มันมี Passwords ตั้งเยอะ ดังนั้นเราจะมาทำให้มันส่งเป็น Automation กัน

---
layout: post
author: Watchanan Chantapakul
title:  "Bandit Level 6 → Level 7"
category: Bandit
tag: Bandit
---

## [โจทย์](https://overthewire.org/wargames/bandit/bandit7.html)
ด่านนี้ให้ทำการค้นหารหัสผ่านเช่นเดิม เพียงแต่รหัสผ่านสำหรับด่านถัดไปนั้นจะถูกเก็บอยู่ในโฟลเดอร์หรือ directory ซ้อน ๆ จำนวนมาก โดยไฟล์เป้าหมายที่มีรหัสผ่านเก็บอยู่ในนั้นมีคุณสมบัติดังนี้
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

ประเด็นก็คือว่าไฟล์ที่เก็บรหัสสามารถถูก **เก็บที่ไหนก็ได้บนเซิร์ฟเวอร์** ไม่ได้จำเป็นต้องอยู่ใน home directory อีกต่อไป

## คำสั่งที่เกี่ยวข้อง
`ls`, `cat`, `file`

## วิธีการ
1. หากเชื่อมต่อ SSH จาก Bandit Level 5 อยู่ ให้ออกจากการเชื่อมต่อโดยกด `Ctrl + c`
2. เชื่อมต่อ SSH เข้าด่านใหม่
    ```
    ssh bandit6@bandit.labs.overthewire.org -p 2220
    ```
    โดยใช้รหัสผ่านคือ**คำตอบของ Bandit Level 6**
3. พยายามลองค้นหาตามตำแหน่งต่าง ๆ ดู ซึ่งตำแหน่งปัจจุบันของสามารถดูได้โดยใช้คำสั่ง `pwd`
4. เราสามารถถอยหลัง directory ขึ้นไปได้ โดยใช้คำสั่ง `cd ..`
5. ทีนี้หากยังหาไฟล์ไม่เจอให้ลองกลับไปนอกสุด ก็คือ root directory (`/`) ใช้คำสั่ง `cd /`
6. คำสั่งในการค้นหาไฟล์ที่มีคุณสมบัติตามต้องการ เราจะใช้การ pipe ผลลัพธ์จากคำสั่ง `find` ไปค้นหาด้วยคำสั่ง `grep` ดังนั้นคำสั่งที่ใส่คุณสมบัติที่ต้องการไปก็จะเป็น
    ```
    find . -type f  -ls | grep 33 | grep bandit6
    ```
7. ผลลัพธ์ของการค้นหาคือดังนี้
    ```
        787922      4 -rw-r-----   1 bandit7  bandit6                 33 May  7  2020 ./var/lib/dpkg/info/bandit7.password
    ```
8. เปิดดูเนื้อหาในไฟล์นั้น ใช้คำสั่ง `cat ./var/lib/dpkg/info/bandit7.password`
8. พบคำตอบ

## คำตอบ
`HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs` (คำตอบอยู่ในไฟล์ ``)

โดยคำตอบข้างบนนี้ก็คือรหัสผ่านในการใช้สำหรับเข้าสู่ SSH ในด่านถัดไป
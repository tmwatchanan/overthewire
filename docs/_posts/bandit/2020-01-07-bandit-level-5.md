---
layout: post
author: Watchanan Chantapakul
title:  "Bandit Level 4 → Level 5"
category: Bandit
tag: Bandit
---

## [โจทย์](https://overthewire.org/wargames/bandit/bandit5.html)
ด่านนี้ให้ทำการค้นหารหัสผ่านเช่นเดิม เพียงแต่รหัสผ่านสำหรับด่านถัดไปนั้นจะถูกเก็บอยู่ในโฟลเดอร์หรือ directory ที่ชื่อว่า `inhere` ซึ่ง**ถูกซ่อน**อยู่ใน home directory อีกทีนึง

## คำสั่งที่เกี่ยวข้อง
`ls`, `cat`, `file`

## วิธีการ
1. หากเชื่อมต่อ SSH จาก Bandit Level 3 อยู่ ให้ออกจากการเชื่อมต่อโดยกด `Ctrl + c`
2. เชื่อมต่อ SSH เข้าด่านใหม่
    ```
    ssh bandit4@bandit.labs.overthewire.org -p 2220
    ```
    โดยใช้รหัสผ่านคือ**คำตอบของ Bandit Level 4**
3. ใช้คำสั่ง `ls` เพื่อดูชื่อไฟล์และ directory จะพบว่ามีไฟล์ทั้งหมด 9 ไฟล์ ได้แก่
    - `-file00`
    - `-file01`
    - `-file02`
    - `-file03`
    - `-file04`
    - `-file05`
    - `-file06`
    - `-file07`
    - `-file08`
    - `-file09`
4. เราต้องเปิดดูเนื้อหาข้างในไฟล์เหล่านี้ด้วยคำสั่ง `cat` ซึ่งหลักการจะเหมือนกับ [Bandit Level 2]({{ site.baseurl }}{% post_url bandit/2020-01-07-bandit-level-2 %}) ซึ่งก็คือไม่สามารถใช้ `cat -file00` ตรง ๆ ได้ ต้องใช้หลักการของ relative path เข้ามาช่วย
5. ใช้คำสั่ง `cd ./-file00` ดูเนื้อหาของไฟล์
6. ใช้คำสั่ง `cd ./-file01` ดูเนื้อหาของไฟล์
7. ...
8. ดูไปเรื่อย ๆ จนพบเนื้อหาที่อ่านออก นั่นแหละคือ flag (ธง) ที่เป็นคำตอบของเรา
9. พบคำตอบ

## คำตอบ
`koReBOKuIDDepwhWk7jZC0RTdopnAYKh` (คำตอบอยู่ในไฟล์ `-file07`)

โดยคำตอบข้างบนนี้ก็คือรหัสผ่านในการใช้สำหรับเข้าสู่ SSH ในด่านถัดไป
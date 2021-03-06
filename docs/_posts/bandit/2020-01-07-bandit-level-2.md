---
layout: post
author: Watchanan Chantapakul
title:  "Bandit Level 1 → Level 2"
category: Bandit
tag: Bandit
---

## [โจทย์](https://overthewire.org/wargames/bandit/bandit2.html)
ในด่านนี้เค้าให้ทำการค้นหารหัสผ่านซึ่งถูกเก็บอยู่ในไฟล์ที่มีชื่อว่า `-` (ขีดเดียวนี่แหละ) ซึ่งมีที่อยู่คือ home directory หรือก็คือ `/home/bandit1`

## คำสั่งที่เกี่ยวข้อง
`ls`, `cat`, `file`

## วิธีการ
1. หากเชื่อมต่อ SSH จาก Bandit Level 0 อยู่ ให้ออกจากการเชื่อมต่อโดยกด `Ctrl + c`
2. เชื่อมต่อ SSH เข้าด่านใหม่
    ```
    ssh bandit1@bandit.labs.overthewire.org -p 2220
    ```
    โดยใช้รหัสผ่านคือ**คำตอบของ Bandit Level 1**
3. ใช้คำสั่ง `ls` เพื่อดูชื่อไฟล์ ก็จะพบว่ามีไฟล์ชื่อ `-` จริง ๆ
4. ตามปกติเราจะใช้ `cat -` เพื่อดูเนื้อหาในไฟล์ แต่ปรากฎว่าเครื่องหมายขีด เป็นเครื่องหมายพิเศษที่คำสั่งต่าง ๆ จะใช้สำหรับส่ง option หรือ flag เข้าไป เช่น `cat --help` ก็ใช้สำหรับดูวิธีการใช้งานคำสั่งนั่นเอง ดังนั้น วิธีการแก้ก็คือใช้ที่อยู่อ้างอิง (relative path)
    - `.` (หรือ จุด) จะหมายถึง โฟลเดอร์ หรือ directory ที่อยู่ปัจจุบัน
    - ดังนั้นเราสามารถใช้ `./-` แทนไฟล์ `-` ได้
    - พิมพ์คำสั่ง `cat ./-` เพื่อดูเนื้อหาไฟล์เลย
5. พบคำตอบ

## คำตอบ
`CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`

โดยคำตอบข้างบนนี้ก็คือรหัสผ่านในการใช้สำหรับเข้าสู่ SSH ในด่านถัดไป
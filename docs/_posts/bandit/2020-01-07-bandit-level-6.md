---
layout: post
author: Watchanan Chantapakul
title:  "Bandit Level 5 → Level 6"
category: Bandit
tag: Bandit
---

## [โจทย์](https://overthewire.org/wargames/bandit/bandit6.html)
ด่านนี้ให้ทำการค้นหารหัสผ่านเช่นเดิม เพียงแต่รหัสผ่านสำหรับด่านถัดไปนั้นจะถูกเก็บอยู่ในโฟลเดอร์หรือ directory ซ้อน ๆ จำนวนมาก โดยไฟล์เป้าหมายที่มีรหัสผ่านเก็บอยู่ในนั้นมีคุณสมบัติดังนี้
- human-readable
- 1033 bytes in size
- not executable

## คำสั่งที่เกี่ยวข้อง
`ls`, `cat`, `file`

## วิธีการ
1. หากเชื่อมต่อ SSH จาก Bandit Level 4 อยู่ ให้ออกจากการเชื่อมต่อโดยกด `Ctrl + c`
2. เชื่อมต่อ SSH เข้าด่านใหม่
    ```
    ssh bandit5@bandit.labs.overthewire.org -p 2220
    ```
    โดยใช้รหัสผ่านคือ**คำตอบของ Bandit Level 5**
3. ใช้คำสั่ง `ls` เพื่อดูชื่อไฟล์และ directory จะพบว่ามี directory ชื่อ `inhere` อยู่ แต่ข้างใน directory นั้นมีไฟล์และ directory อีกมากมาย
4. วิธีการก็คือให้พยายามใช้คำสั่งเช่น `ls` หรือ `find` ในการค้นหาด้วยคุณสมบัติของไฟล์ที่โจทย์ได้กำหนดมา ได้แก่
    - **human-readable** อันนี้ดูจากเนื้อหาไฟล์แล้วสามารถพออ่านออกได้ คือไม่ได้มีเครื่องหมายแปลกประหลาดและรูปแบบไม่เหมือนคำตอบที่ผ่านมา
    - **1033 bytes in size** ขนาดไฟล์มีขนาด 1,033 bytes
    - **not executable** รันไม่ได้ จะสังเกตได้จากเวลาเราใช้คำสั่ง `ls -la` แล้วจะมีสิทธิ์ ([permission](https://www.guru99.com/file-permissions.html#2)) เช่น
        - `-rwxr-x---` แบบนี้มีตัวอักษร x อยู่แสดงว่า executable (รันได้)
        - `-rw-r-----` แบบนี้ไม่มีตัวอักษร x อยู่แสดงว่า not executable (รันไม่ได้)
5. ใช้คำสั่ง `find . -type f  -ls | grep 1033`
6. เมื่อพบชื่อไฟล์ที่ต้องการแล้วก็ใช้คำสั่ง `cat` ดูคำตอบได้เลย
7. พบคำตอบ

## คำตอบ
`DXjZPULLxYr17uwoI01bNLQbtFemEgo7` (คำตอบอยู่ในไฟล์ `maybehere07/.file2`)

โดยคำตอบข้างบนนี้ก็คือรหัสผ่านในการใช้สำหรับเข้าสู่ SSH ในด่านถัดไป
---
layout: post
author: Watchanan Chantapakul
title:  "Bandit Level 2 → Level 3"
category: Bandit
tag: Bandit
---

## [โจทย์](https://overthewire.org/wargames/bandit/bandit3.html)
ด่านนี้ให้ทำการค้นหารหัสผ่านเช่นเดิม เพียงแต่รหัสผ่านสำหรับด่านถัดไปนั้นจะถูกเก็บอยู่ในไฟล์ชื่อ `spaces in this filename` ที่อยู่ใน home directory

## คำสั่งที่เกี่ยวข้อง
`ls`, `cat`, `file`

## วิธีการ
1. หากเชื่อมต่อ SSH จาก Bandit Level 1 อยู่ ให้ออกจากการเชื่อมต่อโดยกด `Ctrl + c`
2. เชื่อมต่อ SSH เข้าด่านใหม่
    ```
    ssh bandit2@bandit.labs.overthewire.org -p 2220
    ```
    โดยใช้รหัสผ่านคือ**คำตอบของ Bandit Level 2**
3. ใช้คำสั่ง `ls` เพื่อดูชื่อไฟล์ ก็จะพบว่ามีไฟล์ชื่อ `spaces in this filename` จริง ๆ
4. ตามปกติเราจะใช้ `cat spaces in this filename` เพื่อดูเนื้อหาในไฟล์ แต่ปรากฎว่าชื่อไฟล์นั้นมีช่องว่าง (space) แทรกอยู่ในชื่อด้วย ดังนั้นการพิมพ์คำสั่งตรง ๆ แบบนั้นจะใช้งานไม่ได้ ดังนั้นเราจะต้องระบุชื่อไฟล์เต็มโดยการครอบเครื่องหมายฟันหนู (double quotes) ไว้แทนข้อความเต็ม
    - พิมพ์คำสั่ง `cat "spaces in this filename"` เพื่อดูเนื้อหาไฟล์เลย
5. พบคำตอบ

## คำตอบ
`UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`

โดยคำตอบข้างบนนี้ก็คือรหัสผ่านในการใช้สำหรับเข้าสู่ SSH ในด่านถัดไป
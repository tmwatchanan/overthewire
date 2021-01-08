---
layout: post
author: Watchanan Chantapakul
title:  "Bandit Level 0"
category: Bandit
tag: Bandit
---

## [โจทย์](https://overthewire.org/wargames/bandit/bandit0.html)
เริ่มเล่นเกม (wargame) โดยการใช้งานเครื่องมือที่เรียกว่า `SSH` (secure shell) โดย [SSH](https://en.wikipedia.org/wiki/SSH_(Secure_Shell)) จะเป็น [protocol](https://en.wikipedia.org/wiki/Communication_protocol) ที่ถูกกำหนดขึ้นมาเพื่อสร้างการเชื่อมต่อ (connection) ระหว่างไคลเอนต์ (client) และ เซิร์ฟเวอร์ (server) ซึ่งโดยปกติ SSH จะใช้หลักการของ [public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography) หรือการเข้ารหัสลับแบบกุญแจสาธารณะ สำหรับในเกม Overthewire นี้ เค้าจะเปิดให้บริการ SSH server ไว้ และเครื่องของเราจะทำหน้าที่เป็น SSH client เพื่อไปเชื่อมต่อเข้ากับเซิร์ฟเวอร์ของเค้า หลักการก็คือจะใช้การสร้างคู่ของกุญแจ public และ private แบบอัตโนมัติทุกตอนที่มีการเชื่อมต่อเพื่อใช้ในการเข้ารหัส และหลังจากนั้นจะให้กรอกรหัสผ่านที่ถูกกำหนดไว้ (pre-defined)

> ซึ่งจริง ๆ แล้วเราสร้างการเชื่อมต่อของ SSH นั้นจะสามารถทำได้อีกวิธีคือ การที่เรากำหนดคู่ของกุญแจ public และ private ไว้เอง อธิบายง่าย ๆ ก็คือ ทาง SSH server จะขอ public key จาก SSH client ไปเก็บไว้ เพื่อทำการเก็บเช็ค (เสมือนกับว่าเป็นบัตรประจำตัว) หากพบว่ามี public key ตรงเวลาสร้างการเชื่อมต่อเข้ามา ก็จะสามารถเข้าใช้งานได้ โดยไม่จำเป็นต้องกรอกรหัสผ่านนั่นเอง

โดยโฮสต์หรือเซิร์ฟเวอร์ SSH ที่เราจะต้องทำการเชื่อมต่อเข้าไปนั่นมีที่อยู่คือ `bandit.labs.overthewire.org` และพอร์ต (port) คือ 2220 เค้าได้มีการสร้างชื่อผู้ใช้ (username) เป็น `bandit0` พร้อมกับรหัสผ่านของผู้ใช้นั้นคือ `bandit0` เช่นเดียวกันไว้เรียบร้อยแล้ว ใน Level 0 นี้เค้าแค่ต้องการให้เราเชื่อมต่อเข้า SSH server ดังกล่าวให้สำเร็จก็เป็นอันเสร็จสิ้น

> โดยปกติ SSH ซึ่งเป็น protocol ที่อยู่ในชั้นแอปพลิเคชัน (Application layer) ในระบบ [OSI model](https://en.wikipedia.org/wiki/OSI_model) จะถูกระบุพอร์ต (port) หมายเลข 22 แต่ SSH server สามารถกำหนดได้ว่าจะให้เป็น port หมายเลขอะไร ดังเช่นในโจทย์นี้ใช้เป็น 2220 แทน

## วิธีการ
1. ติดตั้งโปรแกรม `ssh` (หากยังไม่มี)
2. พิมพ์
    ```sh
    ssh bandit0@bandit.labs.overthewire.org -p 2220
    ```
    เราจะใช้คำสั่ง `ssh` โดยมีรูปแบบดังนี้ ssh `<username>`@`<host>` -p `<port>` ให้แทนที่ค่าต่าง ๆ
    
    - `<username>` เป็นชื่อผู้ใช้
    - `<host>` เป็นที่อยู่ของ SSH server
    - `<port>` เป็นหมายเลขพอร์ตของ SSH
3. เมื่อมีคำพูดว่า
    ```
    bandit0@bandit.labs.overthewire.org's password:
    ```
    ให้กรอกรหัสผ่าน `bandit0` เข้าไป
4. เสร็จสิ้น

## คำตอบ
ไม่มี
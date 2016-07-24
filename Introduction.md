Welcome to Git!!!
===================

## **Introduction**

Git คือ Distributed Version Control System (DVCS) การทำงานแบบไม่ต้องมีศูนย์กลาง จะทำให้การทำงานสามารถ commit ได้เร็ว และสามารถทำงานแบบ offline ได้

การทำงานกับ Git 
- Support command line interface
- มี GUI tools ให้เลือกใช้หลายอัน
- Office Git Site : http://git-scm.com/

สถานะของ Git
- Create file Readme.txt เป็นการสร้าง file ใหม่  `สถานะ untrack`
- Add file เข้าสู่ staging area เป็นการเตรียมพร้อมที่จะทำการ snapshot  `สถานะ staging`
- ทำการ Commit file เป็นการ snapshot file ล่าสุด ข้อมูลถูกบันทึกเรียบร้อยแล้ว  `สถานะ commit`

จากนั้นเมื่อเรามีการแก้ไข file 
- file ที่ถูกแก้ไข สถานะจะเป็น  modified หมายถึง file ของคุณได้ถูกแก้ไขแล้ว แต่ยังไม่ได้มีการยืนยัน `สถานะ modify`
เราต้องทำการ Add file เข้าสู่ staging area เพื่อเตรียมความพร้อมที่จะทำการ snapshot `สถานะ staging` และ commit file เมื่อต้องการบันทึกข้อมูลที่แก้ไขเรียบร้อยแล้วเช่นเดียวกัน `สถานะ commit`

การสร้าง git repository ไปที่ <workdir>/.git/

`cd <work_dir>`
`git init`

การเพิ่ม files เข้า repository (indexing files)

`git add <filename01> <filename02>`add file ที่ชื่อ filename01 กับ filename02

`git add --all` add file ทั้งหมดที่่เป็น new หรือ file ที่ถูก Modify ทั้งหมด

`git add *.txt` add file ที่เป็น file.txt ทั้งหมดที่อยู่ใน current directory

`git add docs/*.txt` add file ใน docs directory ที่เป็น file.txt

`git add docs/`  add file ใน docs directory ทั้งหมด

การตรวจสอบสถานะ repository

`git status`

การ commit repository

`git commit`

`git commit -a` commit แบบไปแก้ใน command line

`git commit -a -m "Modify"` commit message ว่าทำอะไรไป 


## **Staging&Remotes**

การตรวจสอบความแตกต่างระหว่าง version
ใน local repository ว่ามีการแก้ไขอะไรไป

`git diff` 



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

`git commit -a -m "ข้อความอธิบายการเปลี่ยนแปลง"` commit message ว่าทำอะไรไป โดยเป็นการ skip staging กับ commit


## **Staging&Remotes**

การตรวจสอบความแตกต่างระหว่าง versionใน local repository ว่ามีการแก้ไขอะไรไป

`git diff` 

การย้อน working directory ของเราไป ณ commit หนี่งใดใน history ของ local repository

`git reset <id>` ในกรณีที่เราต้องการย้อนไปที่ id ใด id หนึ่ง

`git reset HEAD filename` ในกรณีที่เราต้องการย้อนกลับไปที่ commit ล่าสุด HEAD เป็นการอ้างอิงถึง commit ล่าสุด

ในกรณีที่เราต้องการ discard การเปลี่ยนแปลงจาก file ล่าสุดที่มีการ commit

`git checkout --filename`

การ undo commit

`git reset --soft HEAD^` โดย soft เป็นการ reset ไปที่ staging และ HEAD เป็นการย้อนกลับไป commit ก่อน HEAD

การ add ไปยัง commit

`git add todo.txt`

`git commit --amend -m "New commit message & todo.txt"` โดย amend หมายถึงการ add last commit

Useful command
`git reset --soft HEAD^`  การ undo last commit ไปที่ staging

`git commit --amend -m "New Meassage"` การ change last commit

`git reset --hard HEAD^` การ undo last commit และทั้งหมดที่เปลี่ยนแปลง

`git reset --hard HEAD^^` การ undo 2 last commit และทั้งหมดที่เปลี่ยนแปลง

การ share ข้อมูล

Hosted : GitHub, BitBucket

การ add remote

`git remote add origin http://github.com/Gregg/git-real.git` 

`git remote -v` จะเป็นการ show remote repositories

ส่งการเปลี่ยนแปลงจาก local ไปยัง remote repository (โดยสามารถเปลี่ยนชื่อ master เป็นชื่อ branch ที่ต้องการได้)

`git push origin master` โดยที่ origin คือ remote repository name , master คือ local branch to push

ดึงการเปลี่ยนแปลงล่าสุดมายัง local repository

`git pull`

การทำงานกับ remote

`git remote add <name> <address>` การ add new remote

`git remote rm <name>` การ remove remote

`git push -u <name> <branch>` การ push to remote

## **Cloning&Branching**

การ clone repository

`git clone URL` URL ของ remote repository
`git clone URL localfoldername`

switching to a branch

`git checkout ชื่อbranch`ชื่อ branch ที่เราต้องการ switch ไป HEAD จะเปลี่ยน เช่นจาก master ไปเป็นชื่อbranch ใหม่

working on a branch

  สมมุติเราสร้าง file cat.txt ขึ้นมาที่ branch cat และทำการ commit ที่ branch cat เมื่อเราลอง ls ดูจะมี file README.txt cat.txt
จากนั้นเราจะย้ายกลับไปที่ master branch โดยใช้คำสั่ง `git checkout master`และจากนั้นลอง ls ดูจะพบว่ามีแต่ file README.txt
และลอง `git log` ดูก็จะเห็นแต่ log ของ README.txt ไม่มี log ของ cat.txt คือเป็นการทำงานที่ branch ไหนจะอยู่ที่ branch นั้น

แต่เราสามารถ merge รวมกันได้โดย

time to merge
โดยตอนนี้เราต้องการจะเอา file cat.txt มาที่ branch master ด้วย
ทำได้โดย`git checkout master` ลอง ls ดูจะมี file README.txt อย่างเดียว
จากนั้นใช้คำสั่ง `git merge cat`การทำตรงนี้เรียกว่า `fast forward`เป็นการเชื่อมจาก branch cat ไปยัง branch master
หลังจากนั้นเราสามารถลบ branch cat โดยใช้คำสั่ง `git branch -d cat` โดย d มาจาก delete ทีนี้ก็จะเหลือแต่ branch master

non fast forward 

`git checkout -b admin` คือการ create new branch (branch admin)และ switch ไป branch admin
จากนั้นทำการ add และ commit add และ commit จะเหมือนเป็นการสร้างจุดที่ branch admin 2 จุด
และจากนั้นกลับไปที่ branch master `git checkout master` และใช้คำสั่ง `git branch` จะพบว่ามี 
branch admin และ *master อยู่  โดยจะอยู่คนละเส้นกัน

## **Branching**

Pulling new branch 
`git branch`
`git branch -r` เป็นการ list all remote branch

Remote show
`git remote show origin` 

Removing a branch
`git push origin` เป็นการ delete remote branch
`git branch -d fileที่ต้องการลบ`เป็นการ delete local branch แบบ manual

Tagging
Tag เป็นตัวใช้ reference ในการ commit 
`git tag` list all tage



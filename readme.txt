config

    git config --global user.name 'ps.woramet'
    git config --global user.email 'ps.woramet@gmail.com'

0. สร้างไฟล์ git ใน folder
    
    cmd > git init

1. check file (stage change) in git

    git status

    A = Add
    U = Untracked
    M = Modified

2. add file (stage change) to git

    git add index.html

3. remove file (stage change) from git

    git reset .

4. ตรวสอบการเปลี่ยนแปลงเมื่อ status Modified

    git diff

5. เก็บ (stage change) อีก version

    git commit -m 'add index.html and style.css'

6. ตรวจสอบ log

    git log

---------------------------------------------------------------

การแบ่งการทำงานด้วย branch

default branch จะชื่อ master หรือ main

1. ตรวจสอบ branch ปัจจุบัน

    git branch

2. ทำการสร้าง branch developer พร้อมเปลี่ยนไป branch developer

    (จะทำการนำ stage change ที่เก็บไว้ก่อนหน้ามา)

    git checkout -b developer

3. ย้ายไป branch master

    git checkout master

4. ทำการรวม branch (ไปที่ branch master ก่อน แล้วนำ branch มารวม)

    git checkout master
    git merge developer

    อาจเกิดการชนกันเมื่อมีการแก้ไขไฟล์เดียวกันแล้วนำมา merge กัน

5. git stash (คำสั่งสำหรับเก็บข้อมูล ก่อนย้าย branch หากยังทำงานไม่เสร็จ)

    -เก็บข้อมูลก่อนย้าย branch

        git stash

    -นำข้อมูลที่เก็บมาใช้

        git stash pop

---------------------------------------------------------------

git server

1. การ remote ไปที่ git server โดยใช้ชื่อ origin (ค่า "origin" คือชื่อของ remote repository สามารถตั้งชื่ออื่นได้)

    git remote add origin https://github.com/ps-woramet/Git-Tutorial.git

2. ทำการนำข้อมูล จาก branch master ส่งไปที่ remote repository ที่ชื่อ origin

    git push origin master หรือแบบย่อ git push

3. ทำการนำข้อมูล จากทุก branch ส่งไปที่ remote repository ที่ชื่อ origin

    git push --all origin

4. ทำการดึงข้อมูล จาก remote repository ที่ชื่อ origin มา merge กับ branch ปัจจุบันใน local repository

    git pull origin master

5. ทำการดึงข้อมูล (commits, branches, tags, เป็นต้น) จาก remote repository มายัง local repository โดยไม่ทำการ merge ข้อมูลดังกล่าวเข้ากับ branch ปัจจุบัน

    git fetch

---------------------------------------------------------------

ทำการ pull request แทนการ merge เข้า branch master จากหลายๆคน

1. ทำการสร้าง branch newfeature/user

    git checkout -b 'newfeature/user'

    -สร้างไฟล์ user.html

    -git add user.html

    -git commit -m 'add file user.html'

    -git push origin newfeature/user

2. กด pull request > base master, compare: newfeature/user > create pull request

3. Add a title and Add a description > กด create pull request

4. กด merge pull request (สำหรับคนที่ได้รับอนุญาตในการ merge กับ master)
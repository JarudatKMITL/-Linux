# คู่มือคำสั่ง Linux 

## สารบัญ
1. [คำสั่งพื้นฐานระบบ (Basic System Commands)](#1-คำสั่งพื้นฐานระบบ-basic-system-commands)
2. [การจัดการไฟล์และโฟลเดอร์ (File and Directory Management)](#2-การจัดการไฟล์และโฟลเดอร์-file-and-directory-management)
3. [การจัดการสิทธิ์และความเป็นเจ้าของ (Permissions and Ownership)](#3-การจัดการสิทธิ์และความเป็นเจ้าของ-permissions-and-ownership)
4. [การจัดการโปรเซส (Process Management)](#4-การจัดการโปรเซส-process-management)
5. [การจัดการเครือข่าย (Network Management)](#5-การจัดการเครือข่าย-network-management)
6. [การจัดการผู้ใช้และกลุ่ม (User and Group Management)](#6-การจัดการผู้ใช้และกลุ่ม-user-and-group-management)
7. [การจัดการพื้นที่และดิสก์ (Storage and Disk Management)](#7-การจัดการพื้นที่และดิสก์-storage-and-disk-management)
8. [การบีบอัดและคลายไฟล์ (File Compression)](#8-การบีบอัดและคลายไฟล์-file-compression)
9. [การค้นหาและกรองข้อมูล (Search and Filter)](#9-การค้นหาและกรองข้อมูล-search-and-filter)
10. [การจัดการแพคเกจ (Package Management)](#10-การจัดการแพคเกจ-package-management)
11. [การตั้งค่าระบบ (System Configuration)](#11-การตั้งค่าระบบ-system-configuration)
12. [การดูแลระบบ (System Maintenance)](#12-การดูแลระบบ-system-maintenance)

## 1. คำสั่งพื้นฐานระบบ (Basic System Commands)

### pwd (Print Working Directory)
แสดงตำแหน่งไดเรกทอรีปัจจุบัน

```bash
pwd     # แสดงพาธแบบปกติ
pwd -P  # แสดงพาธจริง (ไม่ใช่ symbolic link)
pwd -L  # แสดงพาธ symbolic link (ค่าเริ่มต้น)
```

### cd (Change Directory)
เปลี่ยนไดเรกทอรี

```bash
cd /path/to/directory  # ไปยังไดเรกทอรีที่ระบุ
cd                     # ไปยังโฮมไดเรกทอรี
cd ~                   # ไปยังโฮมไดเรกทอรี
cd ..                  # ย้อนกลับ 1 ระดับ
cd -                   # กลับไปยังไดเรกทอรีก่อนหน้า
```

### ls (List Directory Contents)
แสดงรายการไฟล์และไดเรกทอรี

```bash
ls              # แสดงรายการพื้นฐาน
ls -l           # แสดงรายละเอียด
ls -a           # แสดงไฟล์ซ่อน
ls -h           # แสดงขนาดในรูปแบบอ่านง่าย
ls -R           # แสดงเนื้อหาในโฟลเดอร์ย่อย
ls -t           # เรียงตามเวลา
ls -S           # เรียงตามขนาด
ls -lah         # รวมหลาย option (-l, -a, -h)
```

ตัวอย่างผลลัพธ์ ls -l:
```
total 32
drwxr-xr-x 2 user group 4096 Jan 29 10:00 Documents
-rw-r--r-- 1 user group 1234 Jan 29 09:45 file.txt
lrwxrwxrwx 1 user group   12 Jan 29 09:30 link -> target
```

### clear
ล้างหน้าจอเทอร์มินัล
```bash
clear   # ล้างหน้าจอ
reset   # รีเซ็ตเทอร์มินัล (แก้ปัญหาการแสดงผลผิดปกติ)
```

### date
แสดงหรือตั้งค่าวันที่และเวลาของระบบ

```bash
date                    # แสดงวันที่และเวลาปัจจุบัน
date +"%Y-%m-%d"        # แสดงในรูปแบบ YYYY-MM-DD
date +"%H:%M:%S"        # แสดงเวลาในรูปแบบ HH:MM:SS
date -s "2025-01-29"   # ตั้งค่าวันที่ (ต้องมีสิทธิ์ root)
```

### cal
แสดงปฏิทิน

```bash
cal              # แสดงเดือนปัจจุบัน
cal 2025        # แสดงปฏิทินทั้งปี 2025
cal 1 2025      # แสดงเดือนมกราคม 2025
cal -3          # แสดง 3 เดือน (เดือนก่อน ปัจจุบัน และถัดไป)
```

### history
แสดงประวัติคำสั่งที่เคยใช้

```bash
history                    # แสดงประวัติทั้งหมด
history 10                 # แสดง 10 รายการล่าสุด
history -c                 # ล้างประวัติ
!100                      # รันคำสั่งลำดับที่ 100
!!                        # รันคำสั่งล่าสุดอีกครั้ง
!string                   # รันคำสั่งล่าสุดที่ขึ้นต้นด้วย "string"
```

### echo
แสดงข้อความหรือค่าตัวแปร

```bash
echo "Hello World"        # แสดงข้อความ
echo $PATH               # แสดงค่าตัวแปร PATH
echo -n "No newline"     # แสดงข้อความโดยไม่ขึ้นบรรทัดใหม่
echo -e "Line1\nLine2"   # แสดงข้อความพร้อม escape sequences
```

### man (Manual)
แสดงคู่มือคำสั่ง

```bash
man ls          # แสดงคู่มือคำสั่ง ls
man -k search   # ค้นหาคำสั่งที่เกี่ยวข้องกับ "search"
man 5 passwd    # แสดงคู่มือ section 5 ของ passwd
```

## 2. การจัดการไฟล์และโฟลเดอร์ (File and Directory Management)

### cp (Copy)
คัดลอกไฟล์หรือไดเรกทอรี

```bash
cp file1 file2           # คัดลอกไฟล์
cp -r dir1 dir2         # คัดลอกไดเรกทอรีและเนื้อหา
cp -i file1 file2       # ถามก่อนเขียนทับ
cp -p file1 file2       # รักษาการตั้งค่าต้นฉบับ (permissions, timestamps)
cp -v file1 file2       # แสดงรายละเอียดระหว่างคัดลอก
cp file1 file2 dir/     # คัดลอกหลายไฟล์ไปยังไดเรกทอรี
cp -a source/ dest/     # คัดลอกแบบ archive (รักษาทุกอย่าง)
```

### mv (Move)
ย้ายหรือเปลี่ยนชื่อไฟล์

```bash
mv file1 file2          # เปลี่ยนชื่อไฟล์
mv file dir/            # ย้ายไฟล์ไปยังไดเรกทอรี
mv -i file1 file2       # ถามก่อนเขียนทับ
mv -v file1 file2       # แสดงรายละเอียดระหว่างย้าย
mv file1 file2 dir/     # ย้ายหลายไฟล์ไปยังไดเรกทอรี
```

### rm (Remove)
ลบไฟล์หรือไดเรกทอรี

```bash
rm file                 # ลบไฟล์
rm -r directory         # ลบไดเรกทอรีและเนื้อหา
rm -f file             # บังคับลบโดยไม่ถาม
rm -i file             # ถามก่อนลบ
rm -v file             # แสดงรายละเอียดระหว่างลบ
rm -rf directory       # บังคับลบไดเรกทอรีและเนื้อหา (ระวัง!)
```

### mkdir (Make Directory)
สร้างไดเรกทอรี

```bash
mkdir dir               # สร้างไดเรกทอรี
mkdir -p a/b/c         # สร้างไดเรกทอรีพร้อมไดเรกทอรีย่อย
mkdir -m 755 dir       # สร้างพร้อมกำหนดสิทธิ์
mkdir dir1 dir2        # สร้างหลายไดเรกทอรี
```

### rmdir (Remove Directory)
ลบไดเรกทอรีที่ว่างเปล่า

```bash
rmdir dir              # ลบไดเรกทอรีที่ว่าง
rmdir -p a/b/c        # ลบไดเรกทอรีและไดเรกทอรีแม่ที่ว่าง
```

### touch
สร้างไฟล์เปล่าหรืออัพเดทเวลาแก้ไข

```bash
touch file            # สร้างไฟล์ใหม่หรืออัพเดทเวลา
touch -a file        # อัพเดทเวลาเข้าถึง
touch -m file        # อัพเดทเวลาแก้ไข
touch -t 202501291200 file  # กำหนดเวลาเฉพาะ
```

### file
ตรวจสอบประเภทไฟล์

```bash
file document.txt     # แสดงประเภทไฟล์
file -i file         # แสดง MIME type
file *               # ตรวจสอบทุกไฟล์ในไดเรกทอรี
```

### dd
คัดลอกและแปลงไฟล์ในระดับต่ำ

```bash
dd if=/dev/zero of=file bs=1M count=100    # สร้างไฟล์ขนาด 100MB
dd if=/dev/sda of=disk.img                 # สร้าง image ของดิสก์
dd if=input of=output conv=ucase           # แปลงเป็นตัวพิมพ์ใหญ่
```

### ln (Link)
สร้างลิงก์ระหว่างไฟล์

```bash
ln file hardlink           # สร้าง hard link
ln -s file symlink        # สร้าง symbolic link
ln -sf target symlink     # สร้าง symbolic link และเขียนทับถ้ามีอยู่
```

## 3. การจัดการสิทธิ์และความเป็นเจ้าของ (Permissions and Ownership)

### chmod (Change Mode)
เปลี่ยนสิทธิ์การเข้าถึงไฟล์

```bash
chmod 755 file           # กำหนดสิทธิ์แบบตัวเลข (rwxr-xr-x)
chmod u+x file          # เพิ่มสิทธิ์ execute ให้ owner
chmod g-w file          # ลบสิทธิ์ write จากกลุ่ม
chmod o=r file          # กำหนดสิทธิ์ read only สำหรับ others
chmod -R 644 dir/       # เปลี่ยนสิทธิ์ทั้งไดเรกทอรี
chmod a+x file          # เพิ่มสิทธิ์ execute ให้ทุกคน
```

ตารางสิทธิ์แบบตัวเลข:
- 4: read (r)
- 2: write (w)
- 1: execute (x)

ตัวอย่างการรวมตัวเลข:
- 7 (4+2+1) = rwx
- 6 (4+2) = rw-
- 5 (4+1) = r-x
- 4 = r--
- 3 (2+1) = -wx
- 2 = -w-
- 1 = --x
- 0 = ---

### chown (Change Owner)
เปลี่ยนเจ้าของไฟล์หรือไดเรกทอรี

```bash
chown user file             # เปลี่ยนเจ้าของ
chown user:group file      # เปลี่ยนทั้งเจ้าของและกลุ่ม
chown -R user dir/         # เปลี่ยนทั้งไดเรกทอรี
chown --reference=file1 file2  # ใช้การตั้งค่าจากไฟล์อ้างอิง
```

### chgrp (Change Group)
เปลี่ยนกลุ่มของไฟล์

```bash
chgrp group file           # เปลี่ยนกลุ่ม
chgrp -R group dir/        # เปลี่ยนทั้งไดเรกทอรี
chgrp --reference=file1 file2  # ใช้การตั้งค่าจากไฟล์อ้างอิง
```

### umask
กำหนดค่าเริ่มต้นสิทธิ์สำหรับไฟล์ใหม่

```bash
umask                      # แสดงค่า umask ปัจจุบัน
umask 022                  # กำหนดค่า umask (ไฟล์ใหม่จะมีสิทธิ์ 644)
umask -S                   # แสดงในรูปแบบสัญลักษณ์
```

## 4. การจัดการโปรเซส (Process Management)

### ps (Process Status)
แสดงโปรเซสที่กำลังทำงาน

```bash
ps                         # แสดงโปรเซสของผู้ใช้ปัจจุบัน
ps aux                     # แสดงโปรเซสทั้งหมดในระบบ
ps -ef                     # แสดงโปรเซสในรูปแบบ full
ps aux | grep nginx        # ค้นหาโปรเซส nginx
ps -u username             # แสดงโปรเซสของผู้ใช้เฉพาะ
ps --sort=-%cpu           # เรียงตามการใช้ CPU
ps --sort=-%mem           # เรียงตามการใช้ Memory
```

ความหมายของคอลัมน์ใน ps aux:
- USER: เจ้าของโปรเซส
- PID: Process ID
- %CPU: เปอร์เซ็นต์การใช้ CPU
- %MEM: เปอร์เซ็นต์การใช้ Memory
- VSZ: Virtual Memory Size
- RSS: Resident Set Size (หน่วยความจำจริง)
- TTY: Terminal type
- STAT: สถานะโปรเซส
- START: เวลาเริ่มต้น
- TIME: เวลา CPU ที่ใช้
- COMMAND: คำสั่งที่รัน

### top
แสดงโปรเซสแบบ real-time

```bash
top                        # แสดงโปรเซสแบบ real-time
top -u username           # แสดงเฉพาะโปรเซสของผู้ใช้
top -p pid1,pid2          # แสดงเฉพาะ PID ที่ระบุ
```

คีย์ลัดใน top:
- M: เรียงตามการใช้ Memory
- P: เรียงตามการใช้ CPU
- N: เรียงตาม PID
- T: เรียงตามเวลาทำงาน
- k: kill โปรเซส (ต้องระบุ PID)
- r: renice โปรเซส (เปลี่ยนความสำคัญ)
- q: ออกจาก top

### kill
ส่งสัญญาณไปยังโปรเซส

```bash
kill pid                   # ส่งสัญญาณ SIGTERM (15)
kill -9 pid               # ส่งสัญญาณ SIGKILL (9)
kill -l                   # แสดงรายการสัญญาณทั้งหมด
killall process_name      # kill ทุกโปรเซสที่ตรงชื่อ
pkill process_name        # เหมือน killall แต่ใช้ pattern matching
```

สัญญาณที่ใช้บ่อย:
- SIGTERM (15): ขอให้โปรเซสจบการทำงาน (default)
- SIGKILL (9): บังคับจบการทำงานทันที
- SIGHUP (1): รีโหลดการตั้งค่า
- SIGSTOP (19): หยุดโปรเซสชั่วคราว
- SIGCONT (18): ทำงานต่อ

### nice และ renice
กำหนดความสำคัญของโปรเซส

```bash
nice -n 10 command        # รันคำสั่งด้วยค่า nice 10
renice -n 10 -p pid      # เปลี่ยนค่า nice ของโปรเซสที่ทำงานอยู่
```

ค่า nice:
- -20 ถึง 19 (-20 = สำคัญมากที่สุด)
- ค่าเริ่มต้น = 0
- ผู้ใช้ทั่วไปกำหนดได้ 0 ถึง 19
- root กำหนดได้ -20 ถึง 19

### jobs, bg, fg
จัดการงานใน shell

```bash
command &                 # รันคำสั่งใน background
jobs                     # แสดงรายการงาน
bg %job_number          # ย้ายงานไป background
fg %job_number          # ย้ายงานมา foreground
Ctrl+Z                   # หยุดงานชั่วคราว
Ctrl+C                   # ยกเลิกงาน

## 5. การจัดการเครือข่าย (Network Management)

### ifconfig / ip
แสดงและตั้งค่าการ์ดเครือข่าย

```bash
ifconfig                      # แสดงการ์ดเครือข่ายทั้งหมด
ifconfig eth0                # แสดงข้อมูล eth0
ip addr show                # แสดงที่อยู่ IP ทั้งหมด
ip link show                # แสดงสถานะการ์ดเครือข่าย

# ตั้งค่า IP address
ifconfig eth0 192.168.1.100  
ip addr add 192.168.1.100/24 dev eth0

# เปิด/ปิดการ์ดเครือข่าย
ifconfig eth0 up/down
ip link set eth0 up/down
```

### ping
ทดสอบการเชื่อมต่อเครือข่าย

```bash
ping host                    # ping ไปยังโฮสต์
ping -c 4 host              # ส่ง 4 packets
ping -i 2 host              # ส่งทุก 2 วินาที
ping -s 1000 host           # กำหนดขนาด packet
ping -w 10 host             # หยุดหลัง 10 วินาที
```

### netstat / ss
แสดงการเชื่อมต่อเครือข่าย

```bash
netstat -tulpn              # แสดง TCP/UDP ports ที่กำลังฟัง
netstat -an                # แสดงการเชื่อมต่อทั้งหมด
netstat -r                 # แสดงตาราง routing
ss -tulpn                  # เหมือน netstat แต่เร็วกว่า
ss -s                      # แสดงสถิติ
```

### traceroute
แสดงเส้นทางไปยังปลายทาง

```bash
traceroute host            # แสดงเส้นทาง
traceroute -n host        # แสดงเป็น IP (ไม่ resolve DNS)
traceroute -m 15 host     # กำหนดจำนวน hops สูงสุด
```

### nslookup / dig
ค้นหาข้อมูล DNS

```bash
nslookup domain.com        # ค้นหา DNS
dig domain.com             # ค้นหาละเอียดกว่า
dig +short domain.com      # แสดงแค่ IP
dig MX domain.com          # ค้นหา mail servers
dig NS domain.com          # ค้นหา name servers
```

### wget / curl
ดาวน์โหลดไฟล์จากอินเทอร์เน็ต

```bash
wget url                   # ดาวน์โหลดไฟล์
wget -c url               # ดาวน์โหลดต่อ
wget -r url               # ดาวน์โหลดทั้งเว็บ
curl url                  # ดาวน์โหลดและแสดงผล
curl -o file url          # บันทึกเป็นไฟล์
curl -I url              # แสดง headers เท่านั้น
```

### scp
คัดลอกไฟล์ผ่าน SSH

```bash
# คัดลอกไปยังเครื่องระยะไกล
scp file user@host:/path/
scp -r dir/ user@host:/path/

# คัดลอกจากเครื่องระยะไกล
scp user@host:/path/file .
scp -r user@host:/path/dir/ .
```

### rsync
ซิงโครไนซ์ข้อมูลระหว่างเครื่อง

```bash
# ซิงค์โฟลเดอร์ในเครื่อง
rsync -av source/ destination/

# ซิงค์กับเครื่องระยะไกล
rsync -av source/ user@host:/path/
rsync -av user@host:/path/ destination/

# options ที่ใช้บ่อย
-a  # archive mode
-v  # verbose
-z  # บีบอัดข้อมูล
-P  # แสดงความคืบหน้าและต่อการส่งได้
--delete  # ลบไฟล์ปลายทางที่ไม่มีในต้นทาง
```

## 6. การจัดการผู้ใช้และกลุ่ม (User and Group Management)

### useradd
เพิ่มผู้ใช้ใหม่

```bash
useradd username           # สร้างผู้ใช้
useradd -m username       # สร้างพร้อม home directory
useradd -G group1,group2 username  # เพิ่มเข้ากลุ่ม
useradd -s /bin/bash username      # กำหนด shell
useradd -c "Full Name" username    # เพิ่มคำอธิบาย
```

### usermod
แก้ไขผู้ใช้ที่มีอยู่

```bash
usermod -G group1,group2 username  # เปลี่ยนกลุ่ม
usermod -aG group username        # เพิ่มกลุ่ม
usermod -s /bin/bash username     # เปลี่ยน shell
usermod -L username              # ล็อคผู้ใช้
usermod -U username              # ปลดล็อคผู้ใช้
```

### userdel
ลบผู้ใช้

```bash
userdel username          # ลบผู้ใช้
userdel -r username      # ลบพร้อม home directory
```

### passwd
จัดการรหัสผ่าน

```bash
passwd                   # เปลี่ยนรหัสผ่านตัวเอง
passwd username         # เปลี่ยนรหัสผ่านผู้ใช้ (root)
passwd -l username      # ล็อครหัสผ่าน
passwd -u username      # ปลดล็อครหัสผ่าน
passwd -S username      # แสดงสถานะรหัสผ่าน
```

### groupadd
เพิ่มกลุ่มใหม่

```bash
groupadd groupname      # สร้างกลุ่ม
groupadd -g 1000 groupname  # กำหนด GID
```

### groupmod
แก้ไขกลุ่ม

```bash
groupmod -n newname oldname  # เปลี่ยนชื่อกลุ่ม
groupmod -g 1001 groupname  # เปลี่ยน GID
```

### groupdel
ลบกลุ่ม

```bash
groupdel groupname      # ลบกลุ่ม
```

### id
แสดงข้อมูล UID และ GID

```bash
id                     # แสดงข้อมูลผู้ใช้ปัจจุบัน
id username           # แสดงข้อมูลผู้ใช้ที่ระบุ
id -u username        # แสดง UID
id -g username        # แสดง primary GID
id -G username        # แสดงทุก GID
```

### w / who / whoami
แสดงผู้ใช้ที่กำลังใช้งานระบบ

```bash
w                      # แสดงผู้ใช้และกิจกรรม
who                    # แสดงผู้ใช้ที่ login
whoami                # แสดงชื่อผู้ใช้ปัจจุบัน
```

## 7. การจัดการพื้นที่และดิสก์ (Storage and Disk Management)

### df
แสดงพื้นที่ดิสก์

```bash
df                     # แสดงพื้นที่ทั้งหมด
df -h                 # แสดงในรูปแบบอ่านง่าย
df -T                 # แสดงประเภทไฟล์ซิสเต็ม
df /path              # แสดงเฉพาะ partition
```

### du
แสดงการใช้พื้นที่

```bash
du file               # แสดงขนาดไฟล์
du -h directory       # แสดงขนาดโฟลเดอร์
du -sh directory     # แสดงขนาดรวม
du -h --max-depth=1   # แสดงเฉพาะระดับแรก
```

### fdisk
จัดการพาร์ติชัน

```bash
fdisk -l              # แสดงพาร์ติชันทั้งหมด
fdisk /dev/sda        # เข้าสู่โหมดแก้ไข
# คำสั่งใน fdisk:
# m - แสดงเมนู
# n - สร้างพาร์ติชันใหม่
# d - ลบพาร์ติชัน
# p - แสดงพาร์ติชัน
# w - บันทึกและออก
# q - ออกโดยไม่บันทึก
```

### mount / umount
เมาท์และยกเลิกการเมาท์

```bash
mount                  # แสดงอุปกรณ์ที่เมาท์
mount /dev/sda1 /mnt  # เมาท์พาร์ติชัน
umount /mnt           # ยกเลิกการเมาท์
```

### mkfs
สร้างระบบไฟล์

```bash
mkfs.ext4 /dev/sda1   # สร้าง ext4
mkfs.ntfs /dev/sda1   # สร้าง NTFS
mkfs.fat /dev/sda1    # สร้าง FAT
```

## 8. การบีบอัดและคลายไฟล์ (File Compression)

### tar
จัดการไฟล์ tar

```bash
# สร้างไฟล์ tar
tar -cvf archive.tar files/    # สร้าง tar
tar -czvf archive.tar.gz files/  # สร้าง tar.gz
tar -cjvf archive.tar.bz2 files/ # สร้าง tar.bz2

# แตกไฟล์ tar
tar -xvf archive.tar         # แตก tar
tar -xzvf archive.tar.gz     # แตก tar.gz
tar -xjvf archive.tar.bz2    # แตก tar.bz2

# options:
# c - create
# x - extract
# v - verbose
# f - file
# z - gzip
# j - bzip2
```

### gzip / gunzip
บีบอัดและคลายไฟล์ .gz

```bash
gzip file              # บีบอัดเป็น .gz
gzip -9 file           # บีบอัดสูงสุด
gzip -d file.gz        # คลายไฟล์ (เหมือน gunzip)
gunzip file.gz         # คลายไฟล์
```

### zip / unzip
จัดการไฟล์ ZIP

```bash
zip archive.zip files          # สร้าง ZIP
zip -r archive.zip directory   # รวมทั้งโฟลเดอร์
unzip archive.zip             # แตกไฟล์ ZIP
unzip -l archive.zip          # ดูรายการไฟล์
```

### rar / unrar
จัดการไฟล์ RAR

```bash
rar a archive.rar files       # สร้าง RAR
rar x archive.rar            # แตกไฟล์ RAR
unrar x archive.rar          # แตกไฟล์ RAR
unrar l archive.rar          # ดูรายการไฟล์
```

## 9. การค้นหาและกรองข้อมูล (Search and Filter)

### find
คำสั่งสำหรับค้นหาไฟล์และไดเรกทอรี

```bash
# ค้นหาพื้นฐาน
find /path -name filename     # ค้นหาตามชื่อ
find /path -type f           # ค้นหาเฉพาะไฟล์
find /path -type d           # ค้นหาเฉพาะไดเรกทอรี

# ค้นหาตามขนาด
find /path -size +100M       # ไฟล์ขนาดใหญ่กว่า 100MB
find /path -size -100M       # ไฟล์ขนาดเล็กกว่า 100MB
find /path -size 100M        # ไฟล์ขนาดเท่ากับ 100MB

# ค้นหาตามเวลา
find /path -mtime +7         # แก้ไขเกิน 7 วัน
find /path -mtime -7         # แก้ไขภายใน 7 วัน
find /path -mmin -60         # แก้ไขภายใน 60 นาที

# ค้นหาและดำเนินการ
find /path -name "*.tmp" -delete            # ลบไฟล์ที่พบ
find /path -type f -exec ls -l {} \;        # แสดงรายละเอียดไฟล์ที่พบ
find /path -name "*.txt" -exec cp {} /backup \;   # คัดลอกไฟล์ที่พบ
```

## 10. การจัดการแพคเกจ (Package Management)

### apt (สำหรับ Debian/Ubuntu)

```bash
# การอัพเดทระบบ
apt update                  # อัพเดทรายการแพคเกจ
apt upgrade                # อัพเกรดแพคเกจทั้งหมด
apt full-upgrade          # อัพเกรดพร้อมลบแพคเกจที่ไม่จำเป็น

# การติดตั้งและลบแพคเกจ
apt install package        # ติดตั้งแพคเกจ
apt remove package        # ลบแพคเกจ
apt purge package         # ลบแพคเกจและไฟล์ตั้งค่า
apt autoremove           # ลบแพคเกจที่ไม่จำเป็น

# การค้นหาและดูข้อมูล
apt search keyword        # ค้นหาแพคเกจ
apt show package         # แสดงข้อมูลแพคเกจ
apt list --installed    # แสดงแพคเกจที่ติดตั้ง
```

### yum/dnf (สำหรับ RHEL/CentOS/Fedora)

```bash
# การอัพเดทระบบ
yum update               # อัพเดททั้งระบบ
yum check-update        # ตรวจสอบอัพเดท

# การติดตั้งและลบแพคเกจ
yum install package     # ติดตั้งแพคเกจ
yum remove package     # ลบแพคเกจ
yum autoremove        # ลบแพคเกจที่ไม่จำเป็น

# การค้นหาและดูข้อมูล
yum search keyword     # ค้นหาแพคเกจ
yum info package      # แสดงข้อมูลแพคเกจ
yum list installed   # แสดงแพคเกจที่ติดตั้ง
```

## 11. การตั้งค่าระบบ (System Configuration)

### การจัดการบริการ (systemctl)

```bash
# การควบคุมบริการ
systemctl start service    # เริ่มบริการ
systemctl stop service    # หยุดบริการ
systemctl restart service # รีสตาร์ทบริการ
systemctl status service  # ดูสถานะบริการ

# การตั้งค่าการเริ่มต้นอัตโนมัติ
systemctl enable service  # เปิดใช้เมื่อบูต
systemctl disable service # ปิดใช้เมื่อบูต

# การดูข้อมูลระบบ
systemctl list-units     # แสดงบริการทั้งหมด
systemctl list-unit-files # แสดงไฟล์บริการ
```

### การจัดการเครือข่าย

```bash
# การตั้งค่า IP
ip addr show                # แสดง IP ทั้งหมด
ip addr add 192.168.1.100/24 dev eth0  # ตั้งค่า IP
ip link set eth0 up/down   # เปิด/ปิดการ์ดเครือข่าย

# การตั้งค่า DNS
cat /etc/resolv.conf      # ดูการตั้งค่า DNS
nmcli device show         # แสดงข้อมูลอุปกรณ์เครือข่าย
```

## 12. การดูแลระบบ (System Maintenance)

### การตรวจสอบระบบ

```bash
# การใช้งานทรัพยากร
top                     # แสดงการใช้งาน CPU และ Memory แบบ real-time
htop                   # เวอร์ชันที่ใช้งานง่ายกว่า top
free -h               # แสดงการใช้งาน Memory
df -h                # แสดงพื้นที่ดิสก์
du -sh /path        # แสดงขนาดไดเรกทอรี

# การตรวจสอบ Log
tail -f /var/log/syslog    # ดู system log แบบ real-time
journalctl                 # ดู systemd journal
journalctl -u service     # ดู log ของบริการ
journalctl -f            # ดู log แบบ real-time

# การตรวจสอบประสิทธิภาพ
vmstat                    # แสดงสถิติ virtual memory
iostat                   # แสดงสถิติ I/O
netstat -tuln           # แสดงพอร์ตที่เปิดใช้งาน
```

### การสำรองข้อมูล

```bash
# การสำรองไฟล์
tar -czf backup.tar.gz /path/to/backup    # สร้างไฟล์สำรอง
tar -xzf backup.tar.gz                   # กู้คืนไฟล์สำรอง

# การ sync ข้อมูล
rsync -av source/ destination/          # sync ข้อมูล
rsync -av --delete source/ destination/ # sync และลบไฟล์ที่ไม่มีในต้นทาง
```

### การดูแลความปลอดภัย

```bash
# การตรวจสอบสิทธิ์
chmod -R 750 /path    # ตั้งค่าสิทธิ์แบบ recursive
chown -R user:group /path  # เปลี่ยนเจ้าของแบบ recursive

# การตรวจสอบการเข้าถึง
last                  # แสดงประวัติการ login
who                  # แสดงผู้ใช้ที่ login อยู่
w                   # แสดงผู้ใช้และกิจกรรม
```

## สรุป Tips & Tricks

1. การใช้ History อย่างมีประสิทธิภาพ:
   ```bash
   !!         # รันคำสั่งล่าสุด
   !n         # รันคำสั่งลำดับที่ n
   !string    # รันคำสั่งล่าสุดที่ขึ้นต้นด้วย string
   ```

2. Shortcuts ที่ควรรู้:
   ```bash
   Ctrl + r    # ค้นหาประวัติคำสั่ง
   Ctrl + a    # ไปต้นบรรทัด
   Ctrl + e    # ไปท้ายบรรทัด
   Ctrl + l    # ล้างหน้าจอ
   ```

3. การใช้ screen หรือ tmux:
   ```bash
   screen -S name   # สร้าง session ใหม่
   screen -r name   # กลับเข้า session
   screen -ls       # แสดง sessions ทั้งหมด
   ```

4. การใช้ alias เพื่อประหยัดเวลา:
   ```bash
   alias ll='ls -la'
   alias update='sudo apt update && sudo apt upgrade'
   ```

## การแก้ปัญหาทั่วไป

1. ปัญหาพื้นที่เต็ม:
   ```bash
   df -h                     # ตรวจสอบพื้นที่
   du -sh /* | sort -hr      # หาไดเรกทอรีที่ใช้พื้นที่มาก
   find / -size +100M        # หาไฟล์ขนาดใหญ่
   ```

2. ปัญหา Memory:
   ```bash
   free -h                   # ตรวจสอบ Memory
   ps aux --sort=-%mem      # แสดงโปรเซสที่ใช้ Memory มาก
   ```

3. ปัญหา CPU:
   ```bash
   top                       # ตรวจสอบการใช้ CPU
   ps aux --sort=-%cpu      # แสดงโปรเซสที่ใช้ CPU มาก
   ```

Version: 2.0
Last Updated: 29/01/2025
Author: IT Support Team

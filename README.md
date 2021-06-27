# 25 bash script example

### 1. Hello bash script

```shell
: '
Cách viết nhiều dòng comment.
Cách viết nhiều dòng comment.
Cách viết nhiều dòng comment.
'
```

### 2. Khai báo biến

```shell
NAME="Tuan"
AGE=18
```

### 3. Ghi nội dung ra màn hình

```shell
echo "Tôi tên là $name, Năm nay tôi $AGE tuổi."
```

### 4. Lấy nội dung nhập vào của người dùng

```shell
echo "Bạn đang công việc gì ?"
read -r job
echo "$job là một công việc tuyệt vời"
```

### 5. Thực hiện tính toàn

```shell
echo "Nhập vào X:"
read -r X
echo "Nhập vào Y"
read -r Y

((sum=X+Y))
echo "Sum: $sum"
```

### 6. Điều kiện rẽ nhánh if, else if, else

```shell
echo "Nhập vào số may mắn của bạn"
read -r n

if [ "$n" -eq 101 ]; then
     echo "Chúc mừng bạn đã đạt giải nhất"
elif [ "$n" -eq 510 ]; then
     echo "Bạn đạt giải nhì"
elif [ "$n" -eq 999 ]; then
     echo "Bạn đạt giải ba"
else
     echo "Chúc bạn may mắn lần sau"
fi
```

### 7. Điều kiện rẽ nhánh case

```shell
echo "Nhập vào số may mắn của bạn"
read -r n

case $n in
     101) echo echo "Chúc mừng bạn đã đạt giải nhất" ;;
     510) echo "Bạn đạt giải nhì" ;;
     999) echo "Bạn đạt giải ba" ;;
     *) echo "Chúc bạn may mắn lần sau" ;;
esac
```

### 8. Khởi tạo và gọi function

```shell
function F1() {
     echo 'I like bash programming'
}

F1
```

### 9. Khởi tạo function nhận tham số đầu vào

```shell
Dien_Tich() {
     area=$(($1 * $2))
     echo "Diện Tích là : $area m2"
}

Dien_Tich 10 20
```

### 10. Khởi tạo function trả về giá trị

```shell
function greeting() {
     str="Hello, $name"
     echo "$str"
}

echo "Enter your name"
read -r name

val=$(greeting)
echo "Return value of the function is $val"
```

### 11. Vòng lặp while

```shell
valid=true
count=1
while [ $valid ]; do
    echo $count

    if [ $count -eq 5 ]; then
        break
    fi

    ((count++))
done
```

### 12. Vòng lặp for

```shell
for (( counter=10; counter>0; counter-- )); do
     echo -n "$counter "
done
printf "\n"
```

### 13. Tạo thư mục

```shell
echo "Enter directory name"
read -r newdir
mkdir "$newdir"
```

### 14. Kiểm tra sự tồn tại của thư mục

```shell
echo "Enter directory name"
read -r ndir

if [ -d "$ndir" ]; then
     echo "Directory exist"
else
     mkdir "$ndir"
     echo "Directory created"
fi
```

### 15. Tạo file

```shell
echo "Enter file name"
read -r newfile
touch "$newfile"
```

### 16. Kiểm tra sự tồn tại của file

```shell
filename=$1
if [ -f "$filename" ]; then
  echo "File exists"
else
  echo "File does not exist"
fi
```

### 17. Đọc nội dụng một file

```shell
file='book.txt'
while read line; do
     echo "$line"
done < $file
```

### 18. Thêm nội dung vào file

```shell
echo "Before appending the file"
cat book.txt

echo "Learning Laravel 5">> book.txt
echo "After appending the file"
cat book.txt
```

### 19. Xoá file

```shell
echo "Enter filename to remove"
read -r fn
rm -i "$fn"
```

### 20. Truyền tham số cho file bash

Tạo file test.sh và lưu trữ đoạn code dưới vào file

```shell
#!/bin/bash
echo "Total arguments : $#"
echo "1st Argument = $1"
echo "2nd argument = $2"
```

terminal exec

```shell
$ bash test.sh Linux Hint
```

### 21. Truyền tham số cho file bash với tham số được gán tên

Tạo file test2.sh và lưu trữ đoạn code dưới vào file

```shell
#!/bin/bash
for arg in "$@"; do
    index=$(echo $arg | cut -f1 -d=)
    val=$(echo $arg | cut -f2 -d=)
    case $index in
        X) x=$val;;
        Y) y=$val;;
        *)
    esac
done

((result=x+y))

echo "X+Y=$result"
```

terminal exec

```shell
$ bash command_line.sh X=20 Y=50
```

### 22. Đọc biến môi trường từ file

```shell
FILE_ENV="./.env"
if [ -f "$FILE_ENV" ]; then
     . "$FILE_ENV"
fi
echo "$ENV"
```

### 23. Lấy thời gian

```shell
Year=$(date +%Y)
Month=$(date +%m)
Day=$(date +%d)
Hour=$(date +%H)
Minute=$(date +%M)
Second=$(date +%S)
echo $(date)
echo "Current Date is: $Day-$Month-$Year"
echo "Current Time is: $Hour:$Minute:$Second"
```

### 24. sleep

```shell
echo "Wait for 5 seconds"
sleep 5
echo "Completed"

```

### 25. send mail

```shell
Recipient="admin@example.com"
Subject="Greeting"
Message="Welcome to our site"
mail -s $Subject $Recipient <<< "$Message"
```
# Hướng dẫn sử dụng v264

V264 là bash script dùng [ffmpeg](https://ffmpeg.org/) để nén video thô sang chuẩn H.264 giảm kích thước file xuống còn 1/10

Mã nguồn V264 rất đơn giản
```bash
#!/bin/bash
if [ -z "$1" ]; then
    echo "You must input video file name"
    exit
fi
if [ -f $1 ]; then
    output="$(echo $1 | sed 's/\.[^.]*$//')"
    ffmpeg -i $1 -c:a copy -x264-params crf=30 -b:a 64k "$output-264.mp4"
else
    echo "File $1 does not exist"
fi
```

Trước tiên hãy tải về file binary ffmpeg và copy vào thư mục \usr\local\bin

Sau đó copy file v264 vào thư mục \usr\local\bin

Cuối cùng là convert file video mp4
```bash
$v264 yourfile.mp4
```
# 1. Tạo Named Volume

```bash
docker volume create easy-volume
docker volume ls
```

# 2. Ghi dữ liệu bằng container thứ nhất

```bash
docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
```

Container được tự động xóa sau khi kết thúc nhờ tùy chọn `--rm`.

# 3. Đọc dữ liệu bằng container thứ hai

```bash
docker run --rm -v easy-volume:/data alpine cat /data/test.txt
```

Kết quả thực tế:

```text
Luu tru du lieu Docker
```

# 4. Nhận xét

Hai container sử dụng chung Named Volume `easy-volume`, được gắn
vào đường dẫn `/data`. Dữ liệu vẫn tồn tại sau khi container thứ nhất
bị xóa, nên container thứ hai có thể đọc lại file `test.txt`.

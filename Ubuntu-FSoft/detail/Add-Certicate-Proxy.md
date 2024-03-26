# Ubuntu&Debian

---

## Đối tượng Áp dụng:

- Máy Linux OS thuộc distrubuted của Debian.
- Như Ubuntu, linuxmint,...

---

## HƯỚNG DẪN CẤU HÌNH ADD CERTICATE

- **Bước 1:** Download tệp tin chứng thực:

| STT | Site        | Link                                                              |
| --- | ----------- | ----------------------------------------------------------------- |
| 1   | Hà Nội      | ...                                                               |
| 2   | Đà Nẵng     | wget https://dn-repo.fsoft.com.vn/misc/certicate/ca-proxy-fdn.cer |
| 3   | Hồ Chí Minh | ...                                                               |

_Bảng. Đường dẫn tương ứng các miền. Sử dụng wget để download hoặc chrome/firefox cũng ok_

- **Bước 2:** Thực thi lệnh sao chép vào thư mục chứng thực store:

```terminal
sudo cp ca-proxy-fdn.cer /usr/local/share/ca-certificates/ca-proxy-fdn.cer
```

- **Bước 3:** Cập nhật lại CA store:

```terminal
 sudo update-ca-certificates
```

**The end**

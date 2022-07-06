
# **Các thư mục quan trọng trong KVM**
- [**Các thư mục quan trọng trong KVM**](#các-thư-mục-quan-trọng-trong-kvm)
  - [1. Thư mục lưu các disk của VM](#1-thư-mục-lưu-các-disk-của-vm)
  - [2. Thư mục chứa các file `.xml` thông số kĩ thuật của VM](#2-thư-mục-chứa-các-file-xml-thông-số-kĩ-thuật-của-vm)
  - [3. Thư mục chứa các file liên quan đến network](#3-thư-mục-chứa-các-file-liên-quan-đến-network)
  - [4. Thư mục lưu các file cấu hình **storage pool**](#4-thư-mục-lưu-các-file-cấu-hình-storage-pool)
  - [5. Thư mục lưu các bản **snapshot**](#5-thư-mục-lưu-các-bản-snapshot)

## 1. Thư mục lưu các disk của VM

- `/var/lib/libvirt/images/` : thư mục lưu các disk của VM

    ![Imgur](https://i.imgur.com/Y74d835.png)

## 2. Thư mục chứa các file `.xml` thông số kĩ thuật của VM 

Đường dẫn thư mục chứ file .XML :

```
cd /etc/libvirt/qemu/
```

![Imgur](https://i.imgur.com/TPnvEUb.png)

Ta có thể sửa file .XML để thay đổi các thông RAM,DICK,CPU :

![Imgur](https://i.imgur.com/sotFA3B.png)

Ta có thể sửa đường dẫn :

![Imgur](https://i.imgur.com/r1bsCQe.png)

## 3. Thư mục chứa các file liên quan đến network

    ![Imgur](https://i.imgur.com/N6jSUnG.png)

- `/etc/libvirt/qemu/networks/` : thư mục chứa các file liên quan đến network :

    ![Imgur](https://i.imgur.com/FJGvcSM.png)

## 4. Thư mục lưu các file cấu hình **storage pool**

- Đường dẫn thư mục lưu các file cấu hình storage pool :

 ```
 /etc/libvirt/storage/
 ```

![Imgur](https://i.imgur.com/Ngc5lkP.png)

## 5. Thư mục lưu các bản **snapshot**

- Đường dẫn thư mục lưu các bản snapshot của các VM :

 ```
 /var/lib/libvirt/qemu/snapshot/
 ``` 

![Imgur](https://i.imgur.com/9UqZ6Xs.png)




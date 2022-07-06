
# **Các thư mục quan trọng trong KVM**

## 1. Thư mục lưu các disk của VM
- `/var/lib/libvirt/images/` : thư mục lưu các disk của VM

    ![Imgur](https://i.imgur.com/Y74d835.png)

## 2. Thư mục chứa các file `.xml` thông số kĩ thuật của VM 
- `/etc/libvirt/qemu/` : thư mục chứa các file `.xml` thông số kĩ thuật của VM :

## 3. thư mục chứa các file liên quan đến network
    ![Imgur](https://i.imgur.com/N6jSUnG.png)

- `/etc/libvirt/qemu/networks/` : thư mục chứa các file liên quan đến network :

    ![Imgur](https://i.imgur.com/FJGvcSM.png)

## 4. Thư mục lưu các file cấu hình storage pool
- `/etc/libvirt/storage/` : thư mục lưu các file cấu hình storage pool :

    ![Imgur](https://i.imgur.com/Ngc5lkP.png)

## 5. Thư mục lưu các bản snapshot của các VM
- `/var/lib/libvirt/qemu/snapshot/` : thư mục lưu các bản snapshot của các VM :

    ![Imgur](https://i.imgur.com/9UqZ6Xs.png)
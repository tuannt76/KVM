
# **Các thư mục quan trọng trong KVM**
- `/var/lib/libvirt/images/` : thư mục lưu các disk của VM

    ![Imgur](https://i.imgur.com/Y74d835.png)

- `/etc/libvirt/qemu/` : thư mục chứa các file `.xml` thông số kĩ thuật của VM :

    ![Imgur](https://i.imgur.com/N6jSUnG.png)

- `/etc/libvirt/qemu/networks/` : thư mục chứa các file liên quan đến network :

    ![Imgur](https://i.imgur.com/FJGvcSM.png)

- `/etc/libvirt/storage/` : thư mục lưu các file cấu hình storage pool :

    [Imgur](https://i.imgur.com/Ngc5lkP.png)

- `/var/lib/libvirt/qemu/snapshot/` : thư mục lưu các bản snapshot của các VM :

    ![Imgur](https://i.imgur.com/9UqZ6Xs.png)
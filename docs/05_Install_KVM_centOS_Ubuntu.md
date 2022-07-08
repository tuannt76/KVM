
- [Cài đặt KVM bằng libvirt](#cài-đặt-kvm-bằng-libvirt)
  - [**1) Cài đặt trên CentOS 7**](#1-cài-đặt-trên-centos-7)
  - [**2) Cài đặt trên Ubuntu**](#2-cài-đặt-trên-ubuntu)
  
# Cài đặt KVM bằng libvirt

## **1) Cài đặt trên CentOS 7**
- **B1 :** Kiểm tra xem **CPU** có hỗ trợ ảo hóa không bằng lệnh sau . Nếu kết quả trả về khác `0` có nghĩa là **CPU** có hỗ trợ :
    ```
    # egrep -c "svm|vmx" /proc/cpuinfo
    2
    ```
Nếu kết quả bằng 0 thì vào setting phần cài đặt tích chọn ô 1 và 2 hoặc 1 và 3,Như trong laptop hiện tại tích chọn 1 và 3  :

![Imgur](https://i.imgur.com/SXDQw9V.png)

- **B2 :** Cài đặt **KVM** và các gói liên quan :
    ```
    # yum install -y qemu-kvm libvirt bridge-utils virt-manager
    ```
    - Trong đó :
        - `qemu-kvm` : phần phụ trợ cho **KVM**
        - `libvirt` : cung cấp libvirt sử dụng để quản lý QEMU và KVM
        - `bridge-utils` : tiện ích sử dụng để tạo vào quản lý các bridge
        - `virt-manager` : cung cấp giao diện để quản lý máy ảo
- **B3 :** Kiểm tra lại xem **KVM** đã được cài vào chưa :
    ```
    # lsmod | grep kvm
    ```
    ![Imgur](https://i.imgur.com/WaIppS9.png)

- **B4 :** Khởi động dịch vụ `libvirt` và cho phép khởi động cùng hệ thống :
    ```
    systemctl start libvirtd
    systemctl enable libvirtd
    ```
- **B5 :** Cài package `virt-install` để cài đặt máy ảo và `virt-viewer` để hiển thị quá trình tạo **VM** :
    ```
    yum install -y virt-install virt-viewer
    ```
    - Đối với **CentOS 7** bản **minimal** cần cài đặt thêm gói `x-window` để sử dụng được `virt-viewer` và `virt-manager` :
        ```
        yum install "@X Window System" xorg-x11-xauth xorg-x11-fonts-* xorg-x11-utils -y
        ```
- **B6 :** Tạo 1 thư mục chứa file `.iso` để cài OS trong đường dẫn `/var/lib/libvirt/`
    ```
    cd /var/lib/libvirt/
    mkdir file-iso
    ```
    - Tải về file iso của **CentOS 7 Minimal** vào thư mục này :
        ```
        cd file-iso
        yum install wget -y
        wget http://mirrors.nhanhoa.com/centos/7.7.1908/isos/x86_64/CentOS-7-x86_64-Minimal-2009.iso
        ```
- **B7 :** Cài máy ảo với các thông số sau :

    ```
    virt-install \
    --name=c776-kvm \
    --vcpus=1 \
    --memory=512 \
    --cdrom=/var/lib/libvirt/file-iso/CentOS-7-x86_64-Minimal-2009.iso \
    --disk=/var/lib/libvirt/images/c776-kvm.qcow2,size=10 \
    --os-variant=rhel7 \
    --network bridge=virbr0
    ```
     ![Imgur](https://i.imgur.com/ZBJo4Yo.png)

    - Trong đó :
        - `--name` :  tên của máy ảo
        - `--vcpus` : số vCPU gán cho máy ảo
        - `--memory` : lượng RAM cấp cho máy ảo ( đơn bị `MiB` )
        - `--cdrom` : chỉ ra đường dẫn đến file `.iso` dùng để cài đặt OS . Nếu boot bằng cách khác dùng option `--location` sau đó chỉ ra đường dẫn đến file (có thể là đường dẫn đến file trên internet)
        - `--disk, size` : chỉ ra vị trí lưu disk máy ảo với disk có size là bao nhiêu ( đơn vị `GiB` )
        - `--os-variant` : loại OS đang tạo. Option này có thể chỉ ra hoặc không nhưng nên sử dụng nó vì nó sẽ cải thiện hiệu năng của máy ảo sau này. Nếu không biết HĐH bạn đang tạo thuộc loại nào, có thể tìm kiếm thông tin này bằng cách dùng lệnh `osinfo-query os`
        - `--network` : loại mạng mà VM sử dụng

**B8 :** Mở một tab SSH khác tới server . Chạy lệnh `virt-manager` để vào trình quản lý cài đặt máy ảo KVM :

    ```
    virt-manager
    ```
**B9** : Ta tiến hành cài đặt máy OS CentOS bình thường :

![Imgur](https://i.imgur.com/o3dFVoU.png)
![Imgur](https://i.imgur.com/9BAgRRs.png)
![Imgur](https://i.imgur.com/AuED87T.png)
![Imgur](https://i.imgur.com/17GoeXD.png)
Quá trình cài đặt hoàn tất :

![Imgur](https://i.imgur.com/VWgIOcP.png)

 **Ở tab cài đặt trước đó** cũng thông báo quá trình cài đặt hoàn tất :

![Imgur](https://i.imgur.com/3cfCm9s.png)


## **2) Cài đặt trên Ubuntu**
- **B1 :** Chuyển đổi sang user `root` :
    ```
    tuannguyen@ubuntu1804~$: sudo -i
    root@ubuntu1804:~#
    ```
- **B2 :** Kiểm tra xem **CPU** có hỗ trợ ảo hóa không bằng lệnh sau . Nếu kết quả trả về khác `0` có nghĩa là **CPU** có hỗ trợ :
    ```
    # egrep -c "svm|vmx" /proc/cpuinfo
    4
    ```
- **B3 :** Cài đặt **KVM** và các gói liên quan :
    ```
    # apt-get update
    # apt-get install -y qemu-kvm libvirt-bin bridge-utils virt-manager
    ```
- **B4 :** Kiểm tra lại xem **KVM** đã được cài vào chưa :
    ```
    # lsmod | grep kvm
    ```
    ![Imgur](https://i.imgur.com/um4c1Ye.png)

- **B5 :** Tạo 1 thư mục chứa file `.iso` để cài OS trong đường dẫn `/var/lib/libvirt/`
    ```
    # cd /var/lib/libvirt/
    # sudo mkdir file-iso
    ```
    - Tải về file iso của **CentOS 7 Minimal** vào thư mục này :
        ```
        # cd file-iso
        # sudo wget http://mirrors.nhanhoa.com/centos/7.7.1908/isos/x86_64/CentOS-7-x86_64-Minimal-1908.iso
        ```
- **B6 :** Cài máy ảo với các thông số sau :
    ```
    virt-install \
    --name=Centos7-vm \
    --vcpus=1 \
    --memory=512 \
    --cdrom=/var/lib/libvirt/file-iso/CentOS-7-x86_64-Minimal-2009.iso \
    --disk=/var/lib/libvirt/images/Centos7-vm,size=3 \
    --os-variant=rhel7 \
    --network bridge=virbr0
    ```

![Imgur](https://i.imgur.com/ZBJo4Yo.png)

    - Trong đó:
        - `--name` : tên cho máy ảo
        - `--vcpus` : số vCPU cấp cho máy ảo
        - `--memory` : dung lượng RAM cấp cho máy ảo (tính bằng `MB`)
        - `--cdrom`: đường dẫn đến file ISO. Nếu muốn boot bằng cách khác ta dùng option `--location` sau đó chỉ ra đường dẫn đến file (có thể là đường dẫn trên internet).
        - `--disk`: chỉ ra vị trí lưu disk của máy ảo. `size` chỉ ra dung lượng disk của máy ảo(tính bằng `GB`)
        - `--os-variant` : chỉ ra kiểu của HĐH của máy ảo đang tạo. Option này có thể chỉ ra hoặc không nhưng nên sử dụng nó vì nó sẽ cải thiện hiệu năng của máy ảo. Nếu bạn không biết HĐH hành của mình thuộc loại nào bạn có thể tìm kiếm thông tin bằng cách dùng lệnh `osinfo-query os`
        - `--network` chỉ ra cách kết nối mạng của máy ảo
    > Tìm hiểu thêm bằng cách sử dụng lệnh `virt-install --help`
- **B7 :** Mở một tab SSH khác tới server . Chạy lệnh `virt-manager` để vào trình quản lý cài đặt máy ảo KVM :
    ```
    # virt-manager
    ```
- **B8 :** Trình quản lý virt-manager hiện lên, chọn vào máy ảo vừa tạo :

    ![Imgur](https://i.imgur.com/hufaFfO.png)

- **B9 :** Cài đặt máy ảo như bình thường :

    ![Imgur](https://i.imgur.com/AuED87T.png)
    ![Imgur](https://i.imgur.com/17GoeXD.png)


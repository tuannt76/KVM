# Tổng quan về Virtualization và Hypervisor

- [Tổng quan về Virtualization và Hypervisor](#tổng-quan-về-virtualization-và-hypervisor)
  - [1. Sự khác biệt giữa virtualization vs Cloud](#1-sự-khác-biệt-giữa-virtualization-vs-cloud)
  - [2.Virtualization](#2virtualization)
    - [2.1) Server Virtualization](#21-server-virtualization)
    - [2.2) Desktop Virtualization](#22-desktop-virtualization)
    - [2.3) Operating System Virtualization](#23-operating-system-virtualization)
    - [2.4) Network functions Virtualization](#24-network-functions-virtualization)
    - [2.5) Storage Virtualization](#25-storage-virtualization)
  - [3) Hypervisors](#3-hypervisors)
    - [3.1) Native of Bare Metal Hypervisor](#31-native-of-bare-metal-hypervisor)
    - [3.2) Hosted Hypervisor](#32-hosted-hypervisor)
  - [4) Hardware Virtualization](#4-hardware-virtualization)
    - [4.1) Virtual CPU](#41-virtual-cpu)
    - [4.2) Virtual Memory](#42-virtual-memory)
    - [4.3) Virtual Storage](#43-virtual-storage)
    - [4.4) Virtual Networking](#44-virtual-networking)
  - [5. Các thành phần và đặc điểm của một hệ thống ảo hóa](#5-các-thành-phần-và-đặc-điểm-của-một-hệ-thống-ảo-hóa)

## 1. Sự khác biệt giữa virtualization vs Cloud

**Virtualization** là một trong các công nghệ nền tảng cho **Cloud-Computing** . Tuy nhiên, **virtualization** không phải là **Cloud-Computing** . **Cloud-Computing** là một dịch vụ mà các nhà cung cấp đưa đến người dùng dựa trên các mức giá khác nhau .
- Trong mạng doanh nghiệp, **virtualization** và **cloud-computing** thường được sử dụng cùng nhau để tạo nên hạ tầng **public cloud** hay **private cloud** .
- Trong các nhu cầu nhỏ hơn, mỗi công nghệ sẽ được triển khai riêng biệt để đạt được những mục đích khác nhau . Theo nhiều cách khác nhau , **virtualization** và **cloud-computing** có thể giúp tiết kiệm các thiết bị đến mức tối thiểu, cũng như sử dụng chúng hiệu quả nhất .
- Các doanh nghiệp hoặc người dùng các nhân thường sử dụng **cloud-computing** bằng cách thuê các dịch vụ **cloud-based** . Các nhà cung cấp dịch vụ **Cloud-Computing** lớn nhất hiện nay là **Microsoft (Azure)** và **Amazon (AWS - Amazon Web Services)**

## 2.Virtualization

- **Virtualization** là một công nghệ cho phép ta cài đặt nhiều hệ điều hành ( **OS** ) khác nhau trên cùng một phần cứng . Chúng hoàn toàn riêng rẽ và độc lập với nhau .
- **Virtualization** ẩn các thông số của tài nguyên phần cứng khỏi các user, các ứng dụng của các OS hoặc người dùng quản lý từng OS . Điều này tương tự như việc biến một tài nguyên vật lý ( như server, hệ điều hành, một ứng dụng hoặc một thiết bị storage ) thành nhiều tài nguyên ảo .
- Các loại **virtualization** :
    - Server Virtualization
    - Desktop Virtualization
    - Operating System Virtualization
    - Network functions Virtualization
    - Storage Virtualization
### 2.1) Server Virtualization
- Đây là dạng ảo hóa hạ tầng server thành nhiều server ảo cho nhiều mục đích khác nhau .

    ![Imgur](https://i.imgur.com/qfLYJPw.png)

### 2.2) Desktop Virtualization
- Tương tự với **server virtualization**, nhưng lần này là dựa trên giao diện người dùng để ảo hóa các Desktop Client .

    ![Imgur](https://i.imgur.com/lDlIF9X.png)

### 2.3) Operating System Virtualization
- Dạng ảo hóa này sẽ cô lập các ứng dụng khỏi hệ điều hành và khỏi các ứng dụng khác , nhằm mục đích tăng khả năng tương thích và khả năng quản lý .
- Một ví dụ điển hình của dạng này là Docker .

    ![Imgur](https://i.imgur.com/TrHfRJM.png)

### 2.4) Network functions Virtualization
- Đây là một phần của cơ sở hạ tầng ảo hóa, đặc biệt được sử dụng khi ảo hóa Server . Giúp ta tạo nên nhiều Switch ảo, các VLan, các mạng NAT, ...

    ![Imgur](https://i.imgur.com/dBQKoxV.png)

### 2.5) Storage Virtualization
- Dạng ảo hóa này được sử dụng rộng rãi trong các DataCenter, khi có một hệ thống lưu trữ lớn và muốn phân chia, gán chúng cho các máy chủ vật lý hoặc máy chủ ảo khác nhau . Việc gán này được thực hiện qua kết nối mạng .
- Hệ thống lưu trữ tổng được gọi là **SAN - Storage Area Network** .

    ![Imgur](https://i.imgur.com/lpmSm11.png)

## 3) Hypervisors
- Một **hypervisor** là một dạng phần mềm cho phép hệ điều hành giao tiếp với phần cứng .
- Chúng cũng được gọi là **Virtual Machine Monitor (VMM)** . 
- **Hypervisor** tạo nên một nền tảng ảo hóa ( ***virtual platform*** ) trên máy chủ , và dựa trên đó các máy ảo hoạt động và được quản lý .
- **Hypervisor** chia thành 2 loại :
    - **Native of Bare Metal Hypervisor**
    Một Hypervisor ở dạng native (hay còn gọi là "bare-metal") **chạy trực tiếp trên phần cứng**. nó nằm giữa phần cứng và một hệ điều hành khách (Guest Operating System). Nó được khởi động trước hệ điều hành và tương tác trực tiếp với kernel. Điều này mang lại **hiệu suất cao nhất** có thể vì *không có hệ điều hành chính* nào *cạnh tranh tài nguyên máy tính* với nó. Tuy nhiên, nó có thể đồng nghĩa với việc hệ thống chỉ có thể sử dụng để chạy các máy ảo vì Hypervisor luôn phải chạy ngầm bên dưới.

Các Hypervisor dạng Native này có hteer kể như : **VMware ESXi, Microsoft Hyper-V và Apple boot Camp.**

    - **Hosted Hypervisor**
    Một Hypervisor dạng Hosted được **cài đặt trên một máy tính** chủ (host computer)
, mà trong đó *có một hệ điều hành đã được cài đặt*. Nó **chạy như một ứng dụng** cũng như các phần mềm khác trên máy tính. Hầu hết các Hypervisor dạng hosted **có thể quản lý và chạy nhiều máy ảo cùng một lúc**. Lợi thế của một Hypervisor hosted là có thể được bật lên hoặc thoát ra khi cần thiết, giải phóng tài nguyên cho máy chủ. Tuy nhiên, vì chạy trên một hệ điều hành, nó có thể đem lại hiệu suất tương tự như một Hypervisor ở dạng Native.
### 3.1) Native of Bare Metal Hypervisor
- **Native Hypervisors** là các hệ phần mềm chạy trực tiếp trên phần cứng của máy chủ để kiểm soát và monitor các máy ảo .
- Các ví dụ điển hình của kiến trúc ảo hóa này là **Oracle VM**, **Microsoft Hyper-V**, **VMWare ESX** và **Xen** .

    ![Imgur](https://i.imgur.com/TKodPss.png)

### 3.2) Hosted Hypervisor
- **Hosted Hypervisor** được thiết kế để có thể chạy được trên các hệ điều hành truyền thống .
- Các hệ điều hành của máy ảo trở thành phần mềm cấp 3 so với phần cứng .
- Các ví dụ điển hình của kiến trúc ảo hóa này là **Oracle VM VirtualBox**, **VMware Workstation**, **KVM**, **QEMU**, **Parallels** .

   ![Imgur](https://i.imgur.com/taU2v01.png)

## 4) Hardware Virtualization
### 4.1) Virtual CPU
- Khi cài đặt một **hypervisor** , mỗi **CPU** vật lý sẽ được tách ra thành các **virtual CPU** . Chúng sẽ chia phần CPU khả dụng ra thành các core ảo và cho phép các **VMs** được sử dụng chung dựa trên core vật lý . 
- Nói chung, **hypervisor** sẽ chỉ định khối lượng công việc phải làm cho mỗi **vCPU** . Nếu máy chủ cần nhiều **CPU** hơn, thì tốt nhất nên triển khai ít **VMs** hơn và trên từng **vCPU** riêng biệt
- Cách tính số lượng **vCPU** :
    - Giả dụ ta có 1 server với 2 **CPU** , mỗi **CPU** có 4 core vật lý . Tổng cộng ta có `2 * 4 = 8` cores vật lý .
    - Dựa trên một vài phép tính toán mà **hypervisor** cung cấp cho mỗi core vật lý , ta có thể có được `5-10` **vCPUs**
    - Tổng cộng ta có từ `40-80` **vCPUs** , có nghĩa là có thể gán tối đã `80` **vCPUs** cho một máy ảo .

        ![Imgur](https://i.imgur.com/Qkykf9R.png)

### 4.2) Virtual Memory
- Chính là **RAM** của máy ảo . Phần cài đặt tài nguyên **RAM** cho máy ảo sẽ quyết định phần **RAM** mà máy chủ sẽ cấp cho các máy ảo . Lượng **RAM** ảo sẽ quyết định có bao nhiêu bộ nhớ khả dụng cho các ứng dụng chạy trên máy ảo .

    ![Imgur](https://i.imgur.com/v3nUXCb.png)

### 4.3) Virtual Storage
- **Storage virtaulization** là 1 nhóm các vùng lưu trữ vật lý ( **Data cluster** ) từ nhiều thiết bị storage kết nối mạng và gộp thành 1 thiết bị lưu trữ được quản lý từ trung tâm . Không thể gán thêm dung lượng lưu trữ cho máy ảo khi **data cluster** không có đủ.
- Các định dạng phổ biến của phần dung lượng gán cho máy ảo là `.vdi`, `vhdx`, `vmdk` và `hdd` .

    ![Imgur](https://i.imgur.com/Dsz3n1s.png)

### 4.4) Virtual Networking
- Các máy ảo trên cùng 1 host trao đổi dữ liệu với nhau dựa trên **vNICs** , kết nối trực tiếp đến các **vSwitch** được tạo ra bởi **hypervisor** .
- Các **vSwitch** giao tiếp với **pNIC** ( card mạng vật lý của host ) giúp các **vNICs** trao đổi dữ liệu ra các mạng bên ngoài, hay Internet ...

    ![Imgur](https://i.imgur.com/UgIpYEk.png)

## 5. Các thành phần và đặc điểm của một hệ thống ảo hóa

* **Tài nguyên vật lý** : Máy chủ vật lý, CPU, RAM, Ổ đĩa cứng, Card mạng.. Nhiệm vụ là chia tài nguyên cấp cho các máy ảo.
* **Phần mềm ảo hóa**(Hypervisor): Cung cấp truy cập cho mỗi máy chủ ảo đến tài nguyên của máy chủ vật lý, Lập kế hoạch phân chia tài nguyên của máy chủ vật lý cho các máy chủ ảo.
* **Hệ điều hành Khách**(Guest Operating System): được cài đặt trên một máy chủ ảo, thao tác như ở trên hệ điều hành thông thường.
* **Máy ảo**(Virtual machine): Nó hoạt động như một máy chủ vật lý thông thường với tài nguyên riêng, giao diện riêng, hệ điều hành riêng.

Đặc điểm của 1 hệ thống ảo hoá :

-  Cho phép tạo tách rời các máy ảo và điều phối truy cập của các máy ảo này đến tài nguyên phần cứng và cấp phát tài nguyên tự động theo nhu cầu sử dụng.
- Nhiều ứng dụng chạy trên 1 server, mỗi VM được lập trình trên máy chủ, do đó nhiều ứng dụng và các hệ điều hành có thể cùng lúc chạy trên host.
- Tối đa hóa công suất sử dụng và tối thiểu hóa server: mỗi máy chủ vật lý Được sử dụng với đầy đủ công suất, cho phép giảm đáng kể chi phí nhờ sử dụng tối đa server.

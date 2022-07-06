# **Tìm Hiểu Cơ chế Thin Provisioning và Thick Provisioning**

- [**Tìm Hiểu Cơ chế Thin Provisioning và Thick Provisioning**](#tìm-hiểu-cơ-chế-thin-provisioning-và-thick-provisioning)
- [**1) Thinly-Provisioned Volumes ( Thin Volumes )**](#1-thinly-provisioned-volumes--thin-volumes-)
- [**2) Thickly-Provisioned Volumes ( Thick Volumes )**](#2-thickly-provisioned-volumes--thick-volumes-)

# **1) Thinly-Provisioned Volumes ( Thin Volumes )**
- **Thin Volume** được tạo ra có 1 dung lượng chia sẵn ( ***allocated size*** ) nhưng chỉ chiếm dung lượng của ổ đĩa đúng bằng dung lượng của dữ liệu thực tế có trên **Volume**  ( ***used size*** ) .
- **VD :** chia ổ ảo `30G` nhưng hiện tại chỉ sử dụng `10G` thì trên ổ đĩa vật lý chỉ chiếm `10G` không gian thực .

    ![Imgur](https://i.imgur.com/TqXvYy2.png)

# **2) Thickly-Provisioned Volumes ( Thick Volumes )**
- **Thick Volume** được tạo ra có 1 dung lượng chia sẵn ( ***allocated size*** ) và chiếm đúng bằng đó dung lượng của ổ đĩa mặc dù dữ liệu bên trong ít hơn .
- **VD :** chia ổ ảo `30G` , thực tế đang sử dụng hết `10G` nhưng trên ổ đĩa vật lý vẫn chiếm `30G` không gian đĩa .

    ![Imgur](https://i.imgur.com/e0wVvkf.png)
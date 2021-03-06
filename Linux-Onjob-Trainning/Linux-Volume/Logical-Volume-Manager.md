# Tìm hiểu về Logical Volume Manager - LVM

## Mục Lục

[Phần 1. Giới thiệu về LVM](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#ph%E1%BA%A7n-1-gi%E1%BB%9Bi-thi%E1%BB%87u-v%E1%BB%81-lvm)

- [1. LVM là gì?](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#1-lvm-l%C3%A0-g%C3%AC-)

- [2. Cấu trúc LVM](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#2-c%E1%BA%A5u-tr%C3%BAc-lvm)

[Phần 2. Tạo và quản lý LVM](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#ph%E1%BA%A7n-2-t%E1%BA%A1o-v%C3%A0-qu%E1%BA%A3n-l%C3%BD-lvm)

- [1. Tạo LVM](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#1-t%E1%BA%A1o-lvm)

- [2. Mở rộng Volume Group và thay đổi kích thước các Logical Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#2-m%E1%BB%9F-r%E1%BB%99ng-volume-group-v%C3%A0-thay-%C4%91%E1%BB%95i-k%C3%ADch-th%C6%B0%E1%BB%9Bc-c%C3%A1c-logical-volume)

- [3. Giảm kích cỡ Logical Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#3-gi%E1%BA%A3m-k%C3%ADch-c%E1%BB%A1-logical-volume)

- [4. Mounting Logical Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#4-mounting-logical-volume)

[Phần 3. Snapshot và restore của Logical Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#ph%E1%BA%A7n-3-snapshot-v%C3%A0-restore-c%E1%BB%A7a-logical-volume)

- [1. Snapshot Logical Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#1-snapshot-logical-volume)

  - [1.1. Tạo Snapshot LVM](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#11-t%E1%BA%A1o-snapshot-lvm)

  - [1.2. Tăng dung lượng snapshot trong LVM](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#12-t%C4%83ng-dung-l%C6%B0%E1%BB%A3ng-snapshot-trong-lvm)

- [2. Restore Logical Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#2-restore-logical-volume)

[Phần 4. Tính năng Thin Provisioning Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#ph%E1%BA%A7n-4-t%C3%ADnh-n%C4%83ng-thin-provisioning-volume)

- [1. Setup Thin Pool và Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#1-setup-thin-pool-v%C3%A0-volume)

  - [1.1. Tạo một Thin Pool](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#11-t%E1%BA%A1o-m%E1%BB%99t-thin-pool)

  - [1.2. Tạo Thin Volume](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#12-t%E1%BA%A1o-thin-volume)

- [3. Tạo file system](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#3-t%E1%BA%A1o-file-system)

[Tài liệu tham khảo](https://github.com/quanganh1996111/Linux-Tutorial/blob/master/Linux-Onjob-Trainning/Linux-Volume/Logical-Volume-Manager.md#t%C3%A0i-li%E1%BB%87u-tham-kh%E1%BA%A3o)

## Phần 1. Giới thiệu về LVM

### 1. LVM là gì ?

LVM là một công cụ để quản lý phân vùng logic được tạo và phân bổ từ các ổ đĩa vật lý. Với LVM bạn có thể dễ dàng tạo mới, thay đổi kích thước hoặc xóa bỏ phân vùng đã tạo.

Với kỹ thuật Logical Volume Manager (LVM), ta có thể thay đổi kích thước mà không cần phải sửa lại partition table của OS. Nếu muốn mở rộng dung lượng của nó, ta chỉ cần ấn định lại dung lượng mà không cần phân vùng lại, cũng không phải đối mặt với nguy cơ mất dữ liệu khi thay đổi dung lượng như khi thao tác trên Partition.

### 2. Cấu trúc LVM

<img src="https://imgur.com/VtGksx7.png">

- **Hard Drives:** Thiết bị lưu trữ dữ liệu. 

- **Partition:** Partitions là các phân vùng của Hard drives, mỗi Hard drives có 4 partition. Có 2 loại Partition:

    - **Primary partition:** Phân vùng chính, có thể khởi động , mỗi đĩa cứng có thể có tối đa 4 phân vùng này.

    - **Extended partition:** Phân vùng mở rộng.

- **Physical Volumes:** Một ổ đĩa vật lý có thể phân chia thành nhiều phân vùng vật lý gọi là Physical Volumes.

- **Volume Group:** Là một nhóm bao gồm nhiều Physical Volume trên 1 hoặc nhiều ổ đĩa khác nhau được kết hợp lại thành một Volume Group. Volume Group được sử dụng để tạo ra các Logical Volume, trong đó người dùng có thể tạo, thay đổi kích thước, lưu trữ, gỡ bỏ và sử dụng.

<img src="https://imgur.com/gHIAFxL.png">

- **Logical Volume:** Một Volume Group được chia nhỏ thành nhiều Logical Volume. Nó được dùng để mount tới hệ thống tập tin (File System) và được format với những chuẩn định dạng khác nhau như ext2, ext3, ext4…

<img src="https://i.imgur.com/UNmyHQI.png">

## Phần 2. Tạo và quản lý LVM

### 1. Tạo LVM

#### Bước 1. Tạo Physical Volume

Để tạo Physical Volume, ta sử dụng lệnh `pvcreate`

```
[root@localhost ~]# pvcreate /dev/sdb /dev/sdc /dev/sdd
  Physical volume "/dev/sdb" successfully created.
  Physical volume "/dev/sdc" successfully created.
  Physical volume "/dev/sdd" successfully created.
```

- Chúng ta có thể liệt kê các danh sách các Physical Volume bằng lệnh `pvs`

- Để xem thông tin chi tiết cho từng Physical Volume, ta dùng lệnh `pvdisplay`. Ví dụ: `pvdisplay /dev/sdb`

#### Bước 2. Tạo Volume Group

Để tạo volume group với tên vg0 bằng cách sử dụng /dev/sdb và /dev/sdc. Chúng ta thực hiện như sau:

```
$ vgcreate new_vol_group /dev/sdd
Volume group "new_vol_group" successfully created
```

Để kiểm tra thông tin của Volume group vừa tạo, ta dùng lệnh `vgdisplay vg0`.

Ý nghĩa các thông tin của Volume group khi chạy lệnh `vgdisplay`:

- VG Name: Tên Volume Group.

- Format: Kiến trúc LVM được sử dụng.

- VG Access: Volume Group có thể đọc/ghi và sẵn sàng để sử dụng.

- VG Status: Volume Group có thể được định cỡ lại, chúng ta có thể mở rộng thêm nếu cần thêm dung lượng.

- PE Size: Mở rộng Physical, Kích thước cho đĩa có thể được xác định bằng kích thước PE hoặc GB, 4MB là kích thước PE mặc định của LVM

- Total PE: Dung lượng Volume Group có

- Alloc PE: Tổng PE đã sử dụng

- Free PE: Tổng PE chưa được sử dụng

Để kiểm tra số lượng Physical Volume dùng để tạo Volume Group, ta dùng lệnh `vgs`.

```
[root@localhost ~]# vgs
  VG   #PV #LV #SN Attr   VSize   VFree
  cl     1   2   0 wz--n- <19.00g     0
  vg0   2   0   0 wz--n-  19.99g 19.99g
```

Trong đó:

- VG: Tên Volume Group

- #PV: Physical Volume sử dụng trong Volume Group

- VFree: Hiển thị không gian trống có sẵn trong Volume Group

- VSize: Tổng kích thước của Volume Group

- #LV: Logical Volume nằm trong volume group

- #SN: Số lượng Snapshot của volume group

- Attr: Trạng thái của Volume group có thể ghi, có thể đọc, có thể thay đổi.

#### Bước 3. Tạo Logical Volume

Chúng ta sẽ tạo 2 Logical Volume với tên `projects` có dung lượng là 10GB và `backups` sử dụng toàn bộ dung lượng còn lại của volume group.

```
[root@localhost ~]# lvcreate -n projects -L 10G vg0
  Logical volume "projects" created.
[root@localhost ~]# lvcreate -n backups -l 100%FREE vg0
  Logical volume "backups" created.
```

Trong đó:

- n: Sử dụng chỉ ra tên của logical volume cần tạo.

- L: Sử dụng chỉ một kích thước cố định.

- l: Sử dụng chỉ phần trăm của không gian còn lại trong volume group.

Kiểm tra danh sách Logical Volume vừa được tạo:

```
[root@localhost ~]# lvs
  LV           VG   Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root         cl   -wi-ao---- <17.00g
  swap         cl   -wi-a-----   2.00g
  backups      vg0  -wi-a-----   9.99g
  projects     vg0  -wi-a-----  10.00g
```

Để hiển thị thông tin chi tiết cho các Logical Volume, ta dùng lệnh `lvdisplay vg0/projects`

#### Bước 4. Tạo File System cho Logical Volume

```
[root@localhost ~]# mkfs.ext4 /dev/vg0/projects
mke2fs 1.42.9 (28-Dec-2013)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
655360 inodes, 2621440 blocks
131072 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2151677952
80 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

[root@localhost ~]# mkfs.ext4 /dev/vg0/backups
mke2fs 1.42.9 (28-Dec-2013)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
655360 inodes, 2619392 blocks
130969 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2151677952
80 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done
```

### 2. Mở rộng Volume Group và thay đổi kích thước các Logical Volume

Trong ví dụ dưới đây chúng ta sẽ thêm một physical volume có tên `/dev/sdd` với kích thước 10GB vào volume group vg0, sau đó chúng ta sẽ tăng kích thước của logical volume `/projects` lên 10GB thực hiện như sau:

- Tạo điểm gắn kết:

```
[root@localhost ~]# mkdir /projects
[root@localhost ~]# mkdir /backups
```

- Mount các Logical Volume vừa tạo:

```
[root@localhost ~]# mount /dev/vg0/projects /projects/
[root@localhost ~]# mount /dev/vg0/backups /backups/
```

- Kiểm tra việc sử dụng không gian ổ đĩa

```
[root@localhost ~]# df -TH
Filesystem               Type      Size  Used Avail Use% Mounted on
/dev/mapper/cl-root      xfs        19G  1.1G   18G   6% /
devtmpfs                 devtmpfs  501M     0  501M   0% /dev
tmpfs                    tmpfs     512M     0  512M   0% /dev/shm
tmpfs                    tmpfs     512M  7.1M  505M   2% /run
tmpfs                    tmpfs     512M     0  512M   0% /sys/fs/cgroup
/dev/sda1                xfs       1.1G  145M  919M  14% /boot
tmpfs                    tmpfs     103M     0  103M   0% /run/user/0
/dev/mapper/vg0-projects ext4      11G   38M   9.9G   1% /projects
/dev/mapper/vg0-backups  ext4      11G   38M   9.9G   1% /backups
```

- Thêm `/dev/sdd` vào Volume Group vg0:

```
[root@localhost ~]# vgextend vg0 /dev/sdd
  Volume group "vg0" successfully extended
```

- Tăng kích thước cho dung lượng Logical Volume `/projects`

```
[root@localhost ~]# lvextend -l +2000 /dev/vg0/projects
  Size of logical volume vg0/projects changed from 10.00 GiB (1920 extents) to 17.81 GiB (4560 extents).
  Logical volume vg0/projects successfully resized.
```

- Sau khi chạy lệnh trên chúng ta cần thay đổi kích thước hệ thống tệp, vì thế chúng ta phải chạy lệnh sau để resize:
    
    - Đối với file system (ext2, ext3, ext 4): `resize2fs`.

    - Đối với file system (xfs): `xfs_growfs`.

```
[root@localhost ~]# resize2fs /dev/vg0/projects
resize2fs 1.42.9 (28-Dec-2013)
Filesystem at /dev/vg0/projects is mounted on /projects; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 2
The filesystem on /dev/vg0/projects is now 4669440 blocks long.

[root@localhost ~]# df -TH
Filesystem               Type      Size  Used Avail Use% Mounted on
/dev/mapper/cl-root      xfs        19G  1.1G   18G   6% /
devtmpfs                 devtmpfs  501M     0  501M   0% /dev
tmpfs                    tmpfs     512M     0  512M   0% /dev/shm
tmpfs                    tmpfs     512M  7.1M  505M   2% /run
tmpfs                    tmpfs     512M     0  512M   0% /sys/fs/cgroup
/dev/sda1                xfs       1.1G  145M  919M  14% /boot
tmpfs                    tmpfs     103M     0  103M   0% /run/user/0
/dev/mapper/vg0-projects ext4       19G   47M   18G   1% /projects
/dev/mapper/vg0-backups   ext4       11G   38M  9.9G   1% /backups
```

### 3. Giảm kích cỡ Logical Volume

Khi chúng ta muốn giảm dung lượng các Logical Volume. Chúng ta cần phải chú ý vì nó rất quan trọng và có thể bị lỗi trong khi chúng ta giảm dung lượng Logical Volume. Để đảm bảo an toàn khi giảm Logical Volume cần thực hiện các bước sau:

- Trước khi bắt đầu, cần sao lưu dữ liệu vì vậy sẽ không phải đau đầu nếu có sự cố xảy ra.

- Để giảm dung lượng Logical Volume, cần thực hiện đầy đủ và cẩn thận 5 bước cần thiết:

    - Ngắt kết nối file system.

    - Kiểm tra file system sau khi ngắt kết nối.

    - Giảm file system.

    - Giảm kích thước Logical Volume hơn kích thước hiện tại.

    - Kiểm tra lỗi cho file system.

    - Mount lại file system và kiểm tra kích thước của nó.

- Khi giảm dung lượng Logical Volume chúng ta phải ngắt kết nối hệ thống tệp trước khi giảm.

Ví dụ: Giảm Logical Volume `project` với kích thước từ 17.81GB giảm xuống còn 10GB mà không làm mất dữ liệu. Chúng ta thực hiện các bước như sau:

Kiểm tra dung lượng của Logical Volume và kiểm tra file system trước khi thực hiện giảm:

```
[root@localhost ~]# lvs
  LV       VG  Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root     cl  -wi-ao---- 17.00g
  swap     cl  -wi-ao----  2.00g
  backups  vg0 -wi-ao---- 10.00g
  projects vg0 -wi-ao---- 17.81g
[root@localhost ~]# df -TH
Filesystem               Type      Size  Used Avail Use% Mounted on
/dev/mapper/cl-root      xfs        19G  6.8G   12G  37% /
devtmpfs                 devtmpfs  501M     0  501M   0% /dev
tmpfs                    tmpfs     512M     0  512M   0% /dev/shm
tmpfs                    tmpfs     512M  7.1M  505M   2% /run
tmpfs                    tmpfs     512M     0  512M   0% /sys/fs/cgroup
/dev/sda1                xfs       1.1G  145M  919M  14% /boot
tmpfs                    tmpfs     103M     0  103M   0% /run/user/0
/dev/mapper/vg0-projects ext4       19G  4.4G   14G  25% /projects
/dev/mapper/vg0-backups  ext4       11G  4.4G  5.6G  44% /backups
```

#### Bước 1. Unount File system

```
[root@localhost ~]# umount /projects/
[root@localhost ~]# df -TH
Filesystem              Type      Size  Used Avail Use% Mounted on
/dev/mapper/cl-root     xfs        19G  6.8G   12G  37% /
devtmpfs                devtmpfs  501M     0  501M   0% /dev
tmpfs                   tmpfs     512M     0  512M   0% /dev/shm
tmpfs                   tmpfs     512M  7.1M  505M   2% /run
tmpfs                   tmpfs     512M     0  512M   0% /sys/fs/cgroup
/dev/sda1               xfs       1.1G  145M  919M  14% /boot
tmpfs                   tmpfs     103M     0  103M   0% /run/user/0
/dev/mapper/vg0-backups ext4       11G  4.4G  5.6G  44% /backups
```

#### Bước 2. Kiểm tra lỗi file system bằng lệnh `e2fsck`

```
[root@localhost ~]# e2fsck -f /dev/vg0/projects
e2fsck 1.42.9 (28-Dec-2013)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/vg0/projects: 11/1171456 files (0.0% non-contiguous), 117573/4669440 blocks
```

#### Bước 3. Giảm kích thước của `projects` theo kích thước từ 17.81GB giảm xuống còn 10GB chúng ta thực hiện như sau:

```
[root@localhost ~]# resize2fs /dev/vg0/projects 10G
resize2fs 1.42.9 (28-Dec-2013)
Resizing the filesystem on /dev/vg0/projects to 2621440 (4k) blocks.
The filesystem on /dev/vg0/projects is now 2621440 blocks long.
```

#### Bước 4. Giảm kích thước `projects` bằng lệnh `lvreduce`

```
[root@localhost ~]# lvreduce -L 10G /dev/vg0/projects
  WARNING: Reducing active logical volume to 10.00 GiB.
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce vg0/projects? [y/n]: y
  Size of logical volume vg0/projects changed from 17.81 GiB (4560 extents) to 10.00 GiB (2560 extents).
  Logical volume vg0/projects successfully resized.
```

#### Bước 5. Để đảm bảo an toàn, kiểm tra lỗi file system đã giảm

```
[root@localhost ~]# e2fsck -f /dev/vg0/projects
e2fsck 1.42.9 (28-Dec-2013)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/vg0/projects: 11/655360 files (0.0% non-contiguous), 83137/2621440 blocks
```

#### Bước 6. Gắn kết file system và kiểm tra kích thước của nó.

```
[root@localhost ~]# mount /dev/vg0/projects /projects/
[root@localhost ~]# lvs
  LV       VG  Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root     cl  -wi-ao---- 17.00g
  swap     cl  -wi-ao----  2.00g
  backups  vg0 -wi-ao---- 10.00g
  projects vg0 -wi-ao---- 10.00g
[root@localhost ~]# df -TH
Filesystem               Type      Size  Used Avail Use% Mounted on
/dev/mapper/cl-root      xfs        19G  6.8G   12G  37% /
devtmpfs                 devtmpfs  501M     0  501M   0% /dev
tmpfs                    tmpfs     512M     0  512M   0% /dev/shm
tmpfs                    tmpfs     512M  7.1M  505M   2% /run
tmpfs                    tmpfs     512M     0  512M   0% /sys/fs/cgroup
/dev/sda1                xfs       1.1G  145M  919M  14% /boot
tmpfs                    tmpfs     103M     0  103M   0% /run/user/0
/dev/mapper/vg0-backups  ext4       11G  4.4G  5.6G  44% /backups
/dev/mapper/vg0-projects ext4       11G  4.4G  5.6G  44% /projects
```

### 4. Mounting Logical Volume

Để thực hiện việc liên kết vĩnh viễn Logical Volume, ta cần phải khai báo UUID của mỗi ổ đĩa trong `/etc/fstab`.

- Kiểm tra UUID:

```
[root@qawordpress ~]# blkid /dev/vg0/projects
/dev/vg0/projects: UUID="e04a6408-c0be-4e37-97ad-bddd2a1ca43a" TYPE="ext4"
[root@qawordpress ~]# blkid /dev/vg0/backups
/dev/vg0/backups: UUID="d4c69ff0-82d4-44f3-adf2-0ce96d6ff1dd" TYPE="ext4"
```

- Thêm các UUID vào `/etc/fstab`:

```
[root@qawordpress ~]# cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Wed Aug 12 16:22:49 2020
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/centos-root /                       ext4    defaults        1 1
UUID=a1499e6c-afb1-4745-981b-bc98f8a12491 /boot                   ext4    defaults        1 2
/dev/mapper/centos-swap swap                    swap    defaults        0 0
UUID=1b5aae9b-d5be-44a0-b4ef-a47a2a9590c8 /projects ext4 defaults 0 0
UUID=a7d4a1e6-d9a7-481b-adad-7c07d684a43b /backups ext4 defaults 0 0
```

Nếu có lỗi, không reboot server để tránh tình trạng server không thể khởi động. Kiểm tra cấu hình trong file `etc/fstab` và chạy lại lệnh cho tới khi không có thông báo lỗi.

## Phần 3. Snapshot và restore của Logical Volume

### 1. Snapshot Logical Volume

#### 1.1. Tạo Snapshot LVM

Kiểm tra không gian trống trong volume group để tạo snapshot:

```
[root@localhost ~]# vgs
  VG     #PV #LV #SN Attr   VSize   VFree
  centos   1   2   0 wz--n- <39.00g     0
  vg0      3   2   0 wz--n- <14.99g <5.00g
```

Sau khi kiểm tra ta thấy `vg0` có khoảng 5GB trống. Tạo một snapshot có tên là snapshot_1 với dung lượng 1GB

```
[root@localhost ~]# lvcreate -L 2GB -s -n snap1 /dev/vg0/backups
  Logical volume "snap1" created.
```

Trong đó:

- `-s`: Tạo snapshot
- `-n`: Tên cho snapshot

Kiểm tra snapshot vừa được tạo:

```
[root@localhost ~]# lvs
  LV       VG     Attr       LSize   Pool Origin  Data%  Meta%  Move Log Cpy%Sync Convert
  root     centos -wi-ao---- <38.00g
  swap     centos -wi-ao----   1.00g
  backups  vg0    owi-aos---   5.99g
  projects vg0    -wi-ao----   4.00g
  snap1    vg0    swi-a-s---   2.00g      backups 0.01
```

Thêm một số tệp vào `dev/vg0/backups` và kiểm tra:

```
[root@localhost ~]# sudo cp -a /var/lib/* /backups/
[root@localhost ~]# lvs
  LV       VG     Attr       LSize   Pool Origin  Data%  Meta%  Move Log Cpy%Sync Convert
  root     centos -wi-ao---- <38.00g
  swap     centos -wi-ao----   1.00g
  backups  vg0    owi-aos---   5.99g
  projects vg0    -wi-ao----   4.00g
  snap1    vg0    swi-a-s---   2.00g      backups 10.79
```

Có khoảng 10.79% dung lượng snapshot đã được sử dụng. Để biết thêm thông tin chi tiết chúng ta sử dụng lệnh sau:

```
[root@localhost ~]# lvdisplay /dev/vg0/snap1
  --- Logical volume ---
  LV Path                /dev/vg0/snap1
  LV Name                snap1
  VG Name                vg0
  LV UUID                iOP6EB-pPSW-rI7w-rgeE-Kgq8-1mKD-bPEy9I
  LV Write Access        read/write
  LV Creation host, time localhost.localdomain, 2020-08-15 15:55:17 +0700
  LV snapshot status     active destination for backups
  LV Status              available
  # open                 0
  LV Size                5.99 GiB
  Current LE             1534
  COW-table size         2.00 GiB
  COW-table LE           512
  Allocated to snapshot  10.93%
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     8192
  Block device           253:6
```

Trong đó ý nghĩa các trường của lệnh `lvdisplay` như sau:

- LV Name: Tên của Snapshot Logical Volume.

- VG Name.: Tên Volume group đang được sử dụng.

- LV Write Access: Snapshot volume ở chế độ đọc và ghi.

- LV Creation host, time: Thời gian khi snapshot được tạo. Nó rất quan trọng vì snapshot sẽ tìm mọi thay đổi sau thời gian này.

- LV snapshot status: Snapshot này thuộc vào logical volume projects.

- LV Size: Kích thước của Source volume mà bạn đã snapshot.

- COW-table size: Kích thước bảng Cow.

- Snapshot chunk size: Cung cấp kích thước của chunk cho snapshot.

Nếu tiếp tục sao chép tệp có dung lượng lớn hơn dung lượng ta cấp cho `snapshot`. Sẽ có lỗi báo:

```
/dev/vg0/snap1: read failed after 0 of 4096 at 10737355714: Input/output error
  /dev/vg0/snap1: read failed after 0 of 4096 at 10737412422: Input/output error
  /dev/vg0/snap1: read failed after 0 of 4096 at 0: Input/output error
  /dev/vg0/snap1: read failed after 0 of 4096 at 4096: Input/output error
  LV          VG  Attr       LSize  Pool Origin   Data%  Meta%  Move Log Cpy%Sync Convert
  root        cl  -wi-ao---- 17.00g
  swap        cl  -wi-ao----  2.00g
  backups     vg0 -wi-ao----  9.99g
  projects    vg0 owi-aos--- 17.81g
  snap1 vg0 swi-I-s---  1.00g      projects 100.00
```

#### 1.2. Tăng dung lượng snapshot trong LVM

Để tăng dung lượng cho snapshot, ta sử dụng lệnh:

```
[root@localhost ~]# lvextend -L +1GB /dev/vg0/snap1
  Size of logical volume vg0/snap1 changed from 2.00 GiB (512 extents) to 3.00 GiB (768 extents).
  Logical volume vg0/snap1 successfully resized.
```

Kiểm tra lại kích thước:

```
[root@localhost ~]# lvdisplay /dev/vg0/snap1
  --- Logical volume ---
  LV Path                /dev/vg0/snap1
  LV Name                snap1
  VG Name                vg0
  LV UUID                iOP6EB-pPSW-rI7w-rgeE-Kgq8-1mKD-bPEy9I
  LV Write Access        read/write
  LV Creation host, time localhost.localdomain, 2020-08-15 15:55:17 +0700
  LV snapshot status     active destination for backups
  LV Status              available
  # open                 0
  LV Size                5.99 GiB
  Current LE             1534
  COW-table size         3.00 GiB
  COW-table LE           768
  Allocated to snapshot  7.29%
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     8192
  Block device           253:6
```

### 2. Restore Logical Volume

Để restore snapshot, chúng ta cần hủy gắn kết hệ thống tệp.

```
[root@localhost ~]# umount /backups/
[root@localhost ~]# df -h
Filesystem                Size  Used Avail Use% Mounted on
devtmpfs                  898M     0  898M   0% /dev
tmpfs                     910M     0  910M   0% /dev/shm
tmpfs                     910M  9.6M  901M   2% /run
tmpfs                     910M     0  910M   0% /sys/fs/cgroup
/dev/mapper/centos-root    38G  1.9G   37G   5% /
/dev/sda1                 976M  165M  745M  19% /boot
tmpfs                     182M     0  182M   0% /run/user/1000
/dev/mapper/vg0-projects  3.9G   16M  3.6G   1% /projects
```

Tiến hành Restore Snapshot:

```
[root@localhost ~]# lvs
  LV       VG     Attr       LSize   Pool Origin  Data%  Meta%  Move Log Cpy%Sync Convert
  root     centos -wi-ao---- <38.00g
  swap     centos -wi-ao----   1.00g
  backups  vg0    owi-a-s---   5.99g
  projects vg0    -wi-ao----   4.00g
  snap1    vg0    swi-a-s---   3.00g      backups 7.29
[root@localhost ~]# lvconvert --merge /dev/vg0/snap1
  Merging of volume vg0/snap1 started.
  vg0/backups: Merged: 92.73%
  vg0/backups: Merged: 95.59%
  vg0/backups: Merged: 98.73%
  vg0/backups: Merged: 100.00%
[root@localhost ~]# lvs
  LV       VG     Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root     centos -wi-ao---- <38.00g
  swap     centos -wi-ao----   1.00g
  backups  vg0    -wi-a-----   5.99g
  projects vg0    -wi-ao----   4.00g
[root@localhost ~]# mount /dev/vg0/backups /backups/
[root@localhost ~]# df -TH
Filesystem               Type      Size  Used Avail Use% Mounted on
devtmpfs                 devtmpfs  942M     0  942M   0% /dev
tmpfs                    tmpfs     954M     0  954M   0% /dev/shm
tmpfs                    tmpfs     954M   11M  944M   2% /run
tmpfs                    tmpfs     954M     0  954M   0% /sys/fs/cgroup
/dev/mapper/centos-root  xfs        41G  2.1G   39G   5% /
/dev/sda1                ext4      1.1G  173M  781M  19% /boot
tmpfs                    tmpfs     191M     0  191M   0% /run/user/1000
/dev/mapper/vg0-projects ext4      4.1G   17M  3.9G   1% /projects
/dev/mapper/vg0-backups  ext4      6.2G   26M  5.9G   1% /backups
```

Kiểm tra lại thư mục `/backups/` để xem kết quả:

```
[root@localhost ~]# cd /backups/
[root@localhost backups]# ls
alternatives  dhclient   logrotate   misc            nginx      plymouth  rpm        stateless  vmware
authconfig    games      lost+found  mysql           os-prober  polkit-1  rpm-state  systemd    yum
dbus          initramfs  machines    NetworkManager  php        postfix   rsyslog    tuned
```

## Phần 4. Tính năng Thin Provisioning Volume

Tính năng này cho phép chúng ta tạo ra số Volume có tổng dung lượng lớn hơn dung lượng cho phép.

### 1. Setup Thin Pool và Volume

Chúng ta tạo 1 Physical Volume `/dev/sde` và sau đó dùng lệnh sau để tạo ra 1 Volume group cho Thin-Pool:

```
[root@localhost ~]# pvcreate /dev/sde
  Physical volume "/dev/sde" successfully created.
[root@localhost ~]# vgcreate vg-thin /dev/sde
  Volume group "vg-thin" successfully created
```

Kiểm tra lại thông tin:

```
[root@localhost ~]# lvs
  LV       VG     Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root     centos -wi-ao---- <38.00g
  swap     centos -wi-ao----   1.00g
  backups  vg0    -wi-ao----   5.99g
  projects vg0    -wi-ao----   4.00g
[root@localhost ~]# vgs
  VG      #PV #LV #SN Attr   VSize   VFree
  centos    1   2   0 wz--n- <39.00g     0
  vg-thin   1   0   0 wz--n-  <5.00g <5.00g
  vg0       3   2   0 wz--n- <14.99g <5.00g
```

#### 1.1. Tạo một Thin Pool

```
[root@localhost ~]# lvcreate -L 4.8GB --thinpool demo vg-thin
  Rounding up size to full physical extent 4.80 GiB
  Thin pool volume with chunk size 64.00 KiB can address at most 15.81 TiB of data.
  Logical volume "demo" created.
```

Trong đó ý nghĩa các tùy chọn:

- `-L`: Kích thước của volume group.

- `--thinpool`: Tạo mới một thinpool.

- `demo`: Tên của thinpool.

- `vg-thin`: Tên của volume group mà chúng ta muốn tạo thinpool.

#### 1.2. Tạo Thin Volume

```
[root@localhost ~]# lvcreate -V 4.8G --thin -n thin-client1 vg-thin/demo
  Rounding up size to full physical extent 4.80 GiB
  Logical volume "thin-client1" created.
[root@localhost ~]# lvs
  LV           VG      Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root         centos  -wi-ao---- <38.00g
  swap         centos  -wi-ao----   1.00g
  demo         vg-thin twi-aotz--   4.80g             0.00   10.64
  thin-client1 vg-thin Vwi-a-tz--   4.80g demo        0.00
  backups      vg0     -wi-ao----   5.99g
  projects     vg0     -wi-ao----   4.00g
```

#### 3. Tạo file system

Tạo file System cho Thin Volume vừa tạo:

```
[root@localhost ~]# mkdir -p /client1
[root@localhost ~]# mkfs.ext4 /dev/vg-thin/thin-client1
mke2fs 1.42.9 (28-Dec-2013)
Discarding device blocks: done
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=16 blocks, Stripe width=16 blocks
315120 inodes, 1258496 blocks
62924 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1289748480
39 block groups
32768 blocks per group, 32768 fragments per group
8080 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

[root@localhost ~]# mount /dev/vg-thin/thin-client1 /client1/
```

Kiểm tra lại xem Volume đã được mount chưa:

```
[root@localhost ~]# df -h
Filesystem                          Size  Used Avail Use% Mounted on
devtmpfs                            898M     0  898M   0% /dev
tmpfs                               910M     0  910M   0% /dev/shm
tmpfs                               910M  9.6M  901M   2% /run
tmpfs                               910M     0  910M   0% /sys/fs/cgroup
/dev/mapper/centos-root              38G  1.9G   37G   5% /
/dev/sda1                           976M  165M  745M  19% /boot
/dev/mapper/vg0-projects            3.9G   16M  3.6G   1% /projects
/dev/mapper/vg0-backups             5.8G  244M  5.3G   5% /backups
tmpfs                               182M     0  182M   0% /run/user/0
/dev/mapper/vg--thin-thin--client1  4.7G   20M  4.4G   1% /client1
```

## Tài liệu tham khảo

https://news.cloud365.vn/lvm-gioi-thieu-ve-logical-volume-manager/

https://blogd.net/linux/tao-va-quan-ly-lvm-trong-linux/

https://vinasupport.com/lvm-la-gi-tao-vao-quan-ly-logical-volume-manager/

https://www.ufsexplorer.com/articles/storage-technologies/lvm-data-organization.php

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/logical_volume_manager_administration/lvm_examples
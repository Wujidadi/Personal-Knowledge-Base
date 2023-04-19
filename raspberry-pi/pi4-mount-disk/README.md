# 在樹莓派 4 上掛載外接硬碟

> 硬體：  
> Raspberry Pi 4 Model B 8GB  
> Kingston XS2000 1TB SSD (以下範例用 xs2000 作為掛載磁區的名稱)

1. `fdisk -l` 確認硬碟代號，假定為 `/dev/sda`
   > 注意：若有區分 boot 區及主磁區，必須掛載主磁區，若硬碟代號為 `/dev/sda`，則主磁區代號應該是 `/dev/sda2`
2. `mkfs -t ext4 /dev/sda` 格式化硬碟
3. `mkdir /mnt/xs2000` 建立掛載資料夾
4. `mount -t auto /dev/sda2 /mnt/xs2000`
5. 離開 `/mnt/xs2000` 後，執行 `umount /mnt/xs2000` 卸載

# VMインスタンスの作成と起動

### Compute Engineの使用可能な公開イメージのリストを取得する

1. イメージリストの取得
```
gcloud compute images list
```

2. イメージがshielded VM機能をサポートしているか確認。  
以下コマンドを実行し、出力に `- type: UEFI_COMPATIBLE` が出力されることを確認する。
```
gcloud compute images describe IMAGE_NAME --project IMAGE_PROJECT
```

### 公開イメージからのVMインスタンスの作成

```
gcloud compute instances create VM_NAME [ --image IMAGE | --image-family IMAGE_FAMILY ] --image-project IMAGE_PROJECT [ --shielded-secure-boot ]
```
- shielded-secure-boot
指定すると3つのshielded VMの機能を有効にしたVMを作成する。

### スナップショットからのVMインスタンスの作成
shielded VMのイメージを基にしたスナップショットの場合、スナップショットから復元した場合は整合性の検証はされない

```
gcloud compute instances create [ INSTANCE_NAME ] --source-snapshot [ BOOT_SNAP_SHOT ] \
--boot-disk-size [ BOOT_DISK_SIZE ] --boot-disk-type [ BOOT_DISK_TYPE ] \
--bood-disk-device-name [ BOOT_DISK_NAME ]
```

- [ INSTANCE_NAME ] 新しいインスタンスの名前
- [ BOOT_SNAP_SHOT ] 復元するブートディスクスナップショットの名前
- [ BOOT_DISK_NAME ] 新しいインスタンスのブートディスクの名前
- [ BOOT_DISK_SIZE ] 新しいインスタンスのブートディスクのサイズ（GB単位）元のスナップショットのサイズより大きくする必要がある
- [ BOOT_DIS_TYPE ] 新しいインスタンスのブートディスクのタイプ。`pd-ssd`または`pd-standard`

非ブートディスク以外を復元する場合は`--create-disk`フラグを追加して`--source-snapshot`を指定する
```
--create-disk source-snapshot=[ SNAPSHOT_NAME ],name=[ DISK_NAME ],size=[ DISK_SIZE ],type=[ DISK_TYPE ]
```

### 新しいインスタンスに非ブートスナップショットを復元する
非ブートスナップショットは、セカンダリ永続ディスクでありインスタンスがデータ保存目的で使用する。  
新しいインスタンスに非ブートスナップショットを復元、または既存のインスタンスに非ブートスナップショットを復元できる。

```
gcloud compute instances create \
    --create-disk source-snapshot=[SNAPSHOT_1_NAME],name=[DISK_1_NAME],size=[DISK_1_SIZE],type=[DISK_1_TYPE] \
    --create-disk source-snapshot=[SNAPSHOT_2_NAME],name=[DISK_2_NAME],size=[DISK_2_SIZE],type=[DISK_2_TYPE]
```

### コンテナイメージからのインスタンスの作成
Compute Engine インスタンスに対してコンテナをデプロイして起動するには、インスタンスを作成する時にコンテナイメージ名とオプションを指定する。

```
gcloud compute instances create-with-container [ INSTANCE_NAME ] --container-image [ CONTAINER_IMAGE ]
```

### 特定のサブネットに所属するVMインスタンスの作成

```
gcloud compute instances create [ INSTANCE_NAME ] --subnet [ SUBNET_NAME ] --zone [ ZONE_NAME ]
```
### shielded VM
Compute Engineの検証可能なインスタンスを提供。  
インスタンスがブートレベル、またはカーネルレベルの改竄がないことを確認できる。
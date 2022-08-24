# Configuring a VM to use Manila Shares

Please note that any items with ***${something}*** are placeholders for your names that you used when you created the manila shares in Horizon or via the CLI.
{: .note}

### 1. Create a mount point on your instance
```
mkdir /mnt/ceph
```

### 2.Configuring your instance

i. Create the file `/etc/ceph.${accessTo}.secret` and add the `accessKey`

Example:

    vi /etc/ceph.manilashare.secret

and add

```
AQAHfhZiwTf/NhAAT5ChE4tDXt3Nq1NyiURbMQ==

```

Substitute the key value from the share creation above.

Also, make sure the permissions on the file are rw to the owner only. You can do that with

    sudo chmod 600 /etc/ceph.manilashare.secret

ii. Edit `/etc/fstab` to include the following line:

```
$path /mnt/ceph ceph name=${accessTo},secretfile=/etc/ceph.${accessTo}.secret,x-systemd.device-timeout=30,x-systemd.mount-timeout=30,noatime,_netdev,rw 0   2
```
$path = IP#:ports followed by volume path (/volume/\_no-group/uuid/uuid)

*Please make sure to change the $variables to whatever you set these values to in Manila or the CLI when you created the share*

Example:

```
149.165.158.38:6789,149.165.158.22:6789,149.165.158.54:6789,149.165.158.70:6789,149.165.158.86:6789:/volumes/_nogroup/fe4f8ad4-2877-4e23-b5d3-46eb8476750b/ab404bac-9584-45f4-8a34-92dfc61fbb98 /mnt/ceph ceph name=manilashare,secretfile=/etc/ceph/ceph.manilashare.secret,x-systemd.device-timeout=30,x-systemd.mount-timeout=30,noatime,_netdev,rw 0   2
```

### 3. Mount the share

Mount the manila share created with the following command `mount -a`

If you then run a `df -h|grep vol` you should see something like this:

> ```149.165.158.38:6789,149.165.158.22:6789,149.165.158.54:6789,149.165.158.70:6789,149.165.158.86:6789:/volumes/_nogroup/fe4f8ad4-2877-4e23-b5d3-46eb8476750b/ab404bac-9584-45f4-8a34-92dfc61fbb98   1.8T  134G  1.7T   2% /mnt/ceph
```

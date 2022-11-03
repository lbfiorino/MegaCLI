# MegaCLI
Raid util MegaCLI (Dell Perc 6/i)

### download

```bash
wget https://docs.broadcom.com/docs-and-downloads/raid-controllers/raid-controllers-common-files/8-07-14_MegaCLI.zip
```

or

```bash
curl -LO https://docs.broadcom.com/docs-and-downloads/raid-controllers/raid-controllers-common-files/8-07-14_MegaCLI.zip
```

### unzip

```bash
unzip 8-07-14_MegaCLI.zip
```

### install package

For Debian

```bash
cd Linux
sudo alien MegaCli-8.07.14-1.noarch.rpm  # convert from rpm to deb first
sudo dpkg -imegacli_8.07.14-2_all.deb
```

For CentOS

```bash
sudo yum install MegaCli-8.07.14-1.noarch.rpm
```

### Create alternatives

For CentOS

```bash
sudo alternatives --install '/usr/bin/MegaCli64' 'MegaCli64' '/opt/MegaRAID/MegaCli/MegaCli64' 1
sudo alternatives --install '/usr/bin/MegaCli' 'MegaCli' '/opt/MegaRAID/MegaCli/MegaCli64' 1
sudo alternatives --install '/usr/bin/megacli' 'megacli' '/opt/MegaRAID/MegaCli/MegaCli64' 1
```

For Debian

```bash
sudo update-alternatives --install '/usr/bin/MegaCli64' 'MegaCli64' '/opt/MegaRAID/MegaCli/MegaCli64' 1
sudo update-alternatives --install '/usr/bin/MegaCli' 'MegaCli' '/opt/MegaRAID/MegaCli/MegaCli64' 1
sudo update-alternatives --install '/usr/bin/megacli' 'megacli' '/opt/MegaRAID/MegaCli/MegaCli64' 1
```

### run MegaCli

```bash
/opt/MegaRAID/MegaCli/MegaCli64 -h
MegaCli64 -h
MegaCli -h
megacli -h
```

## Useful Commands

### Check Virtual Drive Information
```bash
/opt/MegaRAID/MegaCli/MegaCli64 -LDInfo -Lall -aALL
```

### Check physical disks errors
```bash
/opt/MegaRAID/MegaCli/MegaCli64 -PhyErrorCounters -aAll
```

### Check all physical disks
```bash
/opt/MegaRAID/MegaCli/MegaCli64 -PDList -aALL
```

### Check rebuild progress
```bash
# /opt/MegaRAID/MegaCli/MegaCli64 -PDRbld -ShowProg -PhysDrv [Enclosure Device ID:Slot Number] -aAll
/opt/MegaRAID/MegaCli/MegaCli64 -PDRbld -ShowProg -PhysDrv [32:7] -aAll
# or
/opt/MegaRAID/MegaCli/MegaCli64 -PDRbld -ProgDsply -PhysDrv [32:7] -aAll
```

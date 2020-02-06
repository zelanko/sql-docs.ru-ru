---
title: Настройка экземпляра отказоустойчивого кластера хранилища iSCSI — SQL Server на Linux
description: Узнайте, как настроить экземпляр отказоустойчивого кластера с помощью iSCSI для SQL Server на Linux.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: e10f354a8f0af2467a9519a794995043864a4cd6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75558594"
---
# <a name="configure-failover-cluster-instance---iscsi---sql-server-on-linux"></a>Настройка экземпляра отказоустойчивого кластера (iSCSI) — SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается, как настроить хранилище iSCSI для экземпляра отказоустойчивого кластера в Linux. 

## <a name="configure-iscsi"></a>Настройка iSCSI 
iSCSI использует сетевые подключения для представления дисков с сервера, который является целью для серверов. Для серверов, подключающихся к цели iSCSI, требуется настроить инициатор iSCSI. Дискам на цели присваиваются явные разрешения, чтобы обратиться к ним могли только инициаторы, обладающие соответствующими правами. Цель должна обладать высокой доступностью и надежностью.

### <a name="important-iscsi-target-information"></a>Важные сведения о цели iSCSI
Хотя в этом разделе не рассматривается настройка цели iSCSI, так как она зависит от типа используемого источника, убедитесь, что настроены параметры безопасности для дисков, которые будут использоваться узлами кластера.  

Цель никогда не следует настраивать на любом из узлов экземпляра отказоустойчивого кластера, если используется цель iSCSI на базе Linux. Для повышения производительности и доступности сети iSCSI должны быть отделены от тех, по которым передается обычный сетевой трафик, как на исходном, так и на клиентском сервере. Сети, используемые для iSCSI, должны быть быстрыми. Помните, что сеть потребляет некоторую пропускную способность процессора, поэтому при использовании обычного сервера следует проводить соответствующее планирование.
Важнее всего убедиться в том, что созданным дискам назначены соответствующие разрешения, чтобы к ним могли обратиться только серверы, участвующие в экземпляре отказоустойчивого кластера. Ниже показан пример из цели iSCSI, где linuxnodes1 — это созданное имя, а IP-адреса узлов назначены, чтобы NewFCIDisk1.vhdx был им виден.

![Инициатор][1]

### <a name="instructions"></a>Instructions

В этом разделе рассматривается настройка инициатора iSCSI на серверах, которые будут служить узлами для экземпляра отказоустойчивого кластера. Эти инструкции должны работать и в RHEL и Ubuntu.

Дополнительные сведения об инициаторе iSCSI для поддерживаемых дистрибутивов см. по следующим ссылкам.
- [Red Hat](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/iscsi-api.html)
- [SUSE](https://www.suse.com/documentation/sles11/stor_admin/data/sec_inst_system_iscsi_initiator.html) 
- [Ubuntu](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

1.  Выберите один из серверов, которые будут включены в конфигурацию экземпляра отказоустойчивого кластера. Какой именно — не имеет значения. iSCSI должен находиться в выделенной сети, поэтому настройте iSCSI для распознавания и использования этой сети. Запустите `sudo iscsiadm -m iface -I <iSCSIIfaceName> -o new`, где `<iSCSIIfaceName>` — это уникальное или понятное имя для сети. В следующем примере используется `iSCSINIC`.
   
    ```bash
    sudo iscsiadm -m iface -I iSCSINIC -o new
    ```
    ![7-setiscsinetwork][6]
 
2.  Измените `/var/lib/iscsi/ifaces/iSCSIIfaceName`. Убедитесь, что в нем полностью заполнены следующие значения.

    - iface.net_ifacename — это имя сетевой карты, отображаемое в операционной системе.
    - iface.hwaddress — это MAC-адрес уникального имени, которое будет создано для этого интерфейса ниже.
    - iface.ipaddress
    - iface.subnet_Mask 

    См. следующий пример.

    ![iSCSITargetSettings][2]

3.  Найдите цель iSCSI.

    ```bash
    sudo iscsiadm -m discovery -t sendtargets -I <iSCSINetName> -p <TargetIPAddress>:<TargetPort>
    ```

     \<iSCSINetName> — это уникальное/понятное имя для сети, \<TargetIPAddress> — это IP-адрес цели iSCSI, а \<TargetPort> — это порт цели iSCSI. 

    ![iSCSITargetResults][3]

 
4.  Войдите на цель.

    ```bash
    sudo iscsiadm -m node -I <iSCSIIfaceName> -p TargetIPAddress -l
    ```

    \<iSCSIIfaceName> — это уникальное/понятное имя для сети, а \<TargetIPAddress> — это IP-адрес цели iSCSI.

    ![iSCSITargetLogin][4]

5.  Проверьте наличие подключения к цели iSCSI.

    ```bash
    sudo iscsiadm -m session
    ```

    ![iSCSIVerify][5]

 
6.  Проверьте подключенные к iSCSI диски.

    ```bash
    sudo grep "Attached SCSI" /var/log/messages
    ```
    ![30-iSCSIattachedDisks][7]

7.  Создайте физический том на диске iSCSI.

    ```bash
    sudo pvcreate /dev/<devicename>
    ```

    \<devicename> — это имя устройства из предыдущего шага. 

 
8.  Создайте группу томов на диске iSCSI. Диски, назначенные одной группе томов, отображаются в виде пула или коллекции. 

    ```bash
    sudo vgcreate <VolumeGroupName> /dev/devicename
    ```

    \<VolumeGroupName> — это имя группы томов, а \<devicename> — это имя устройства из шага 6. 
 
9.  Создайте и проверьте логический том для диска.

    ```bash
    sudo lvcreate -Lsize -n <LogicalVolumeName> <VolumeGroupName>
    ```
    
    \<size> — это размер создаваемого тома, для которого можно указать G (гигабайты), T (терабайты) и т. п., \<LogicalVolumeName> — это имя логического тома, а \<VolumeGroupName> — это имя группы томов из предыдущего шага. 

    В приведенном ниже примере создается том размером 25 ГБ.
 
    ![Create25GBVol][10]

10. Выполните `sudo lvs`, чтобы просмотреть созданный LVM.
 
11. Отформатируйте логический том с использованием поддерживаемой файловой системы. Для EXT4 используйте следующий пример.

    ```bash
    sudo mkfs.ext4 /dev/<VolumeGroupName>/<LogicalVolumeName>
    ```

    \<VolumeGroupName> — это имя группы томов из предыдущего шага. \<LogicalVolumeName> — это имя логического тома из предыдущего шага.  

12. Для системных баз данных или других объектов, хранящихся в расположении данных по умолчанию, выполните указанные ниже действия. В противном случае перейдите к шагу 13.

   *    Убедитесь в том, что SQL Server остановлен на сервере, на котором вы работаете.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Перейдите в режим суперпользователя. В случае успешного действия подтверждение не выводится.

    ```bash
    sudo -i
    ```

   *    Переключитесь на пользователя mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    su mssql
    ```

   *    Создайте временный каталог для хранения данных и файлов журналов SQL Server. В случае успешного действия подтверждение не выводится.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir> — это имя папки. В приведенном ниже примере создается папка /var/opt/mssql/TempDir.

    ```bash
    mkdir /var/opt/mssql/TempDir
    ```
    
   *    Скопируйте данные и файлы журналов SQL Server во временный каталог. В случае успешного действия подтверждение не выводится.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir> — это имя папки из предыдущего шага.
    
   *    Проверьте наличие файлов в папке.

    ```bash
    ls \<TempDir>
    ```
    \<TempDir> — это имя папки из шага d.

   *    Удалите файлы из существующего каталога данных SQL Server. В случае успешного действия подтверждение не выводится.

    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   *    Проверьте, были ли файлы удалены. На рисунке ниже показан пример всей последовательности с c по h.

    ```bash
    ls /var/opt/mssql/data
    ```

    ![45-CopyMove][8]
 
   *    Введите `exit`, чтобы переключиться на привилегированного пользователя.

   *    Подключите логический том iSCSI в папке данных SQL Server. В случае успешного действия подтверждение не выводится.

    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> /var/opt/mssql/data
    ``` 

    \<VolumeGroupName> — это имя группы томов, а \<LogicalVolumeName> — это имя созданного логического тома. Приведенный ниже пример синтаксиса соответствует группе томов и логическому тому из предыдущей команды.

    ```bash
    mount /dev/FCIDataVG1/FCIDataLV1 /var/opt/mssql/data
    ``` 

   *    Измените владельца подключения на mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    chown mssql /var/opt/mssql/data
    ```

   *    Измените владельца группы подключения на mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    chgrp mssql /var/opt/mssql/data
    ``` 

   *    Переключитесь на пользователя mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    su mssql
    ``` 

   *    Скопируйте файлы из временного каталога /var/opt/mssql/data. В случае успешного действия подтверждение не выводится.

    ```bash
    cp /var/opt/mssql/TempDir/* /var/opt/mssql/data
    ``` 

   *    Проверьте наличие файлов.

    ```bash
    ls /var/opt/mssql/data
    ``` 
 
   *    Введите `exit`, чтобы выйти из учетной записи mssql.
    
   *    Введите `exit`, чтобы выйти из учетной записи привилегированного пользователя.

   *    Запустите SQL Server. Если все данные были скопированы и параметры безопасности применены правильно, сервер SQL Server должен отобразиться как запущенный.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ``` 
 
   *    Остановите сервер SQL Server и убедитесь в том, что его работа прекращена.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ``` 

13. Для объектов, отличных от системных баз данных, например пользовательских баз данных или резервных копий, выполните указанные ниже действия. Если используется только расположение по умолчанию, перейдите к шагу 14.

   *    Перейдите в режим суперпользователя. В случае успешного действия подтверждение не выводится.

    ```bash
    sudo -i
    ```

   *    Создайте папку, которая будет использоваться сервером SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<FolderName> — это имя папки. Если папка находится в другом месте, необходимо указать полный путь к ней. В приведенном ниже примере создается папка /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    Подключите логический том iSCSI в папке, созданной в предыдущем шаге. В случае успешного действия подтверждение не выводится.
    
    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName> — это имя группы томов, \<LogicalVolumeName> — это имя созданного логического тома, а \<FolderName> — это имя папки. Пример синтаксиса показан ниже.

    ```bash
    mount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

   *    Измените владельца созданной папки на mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    chown mssql <FolderName>
    ```

    \<FolderName> — это имя созданной папки. Ниже приведен пример такого файла.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```
  
   *    Измените владельца группы папки на mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    chown mssql <FolderName>
    ```

    \<FolderName> — это имя созданной папки. Ниже приведен пример такого файла.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```

   *    Введите `exit`, чтобы выйти из режима суперпользователя.

   *    Создайте в этой папке базу данных для тестирования. В примере ниже создается база данных с помощью sqlcmd, переключается контекст, проверяется наличие файлов на уровне ОС, а затем временная папка удаляется. Можно также использовать SSMS.
  
    ![50-ExampleCreateSSMS][9]

   *    Отключение общей папки 

    ```bash
    sudo umount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName> — это имя группы томов, \<LogicalVolumeName> — это имя созданного логического тома, а \<FolderName> — это имя папки. Пример синтаксиса показан ниже.

    ```bash
    sudo umount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

14. Настройте сервер таким образом, чтобы группу томов мог активировать только Pacemaker.

    ```bash
    sudo lvmconf --enable-halvm --services -startstopservices
    ```
 
15. Создайте список групп томов на сервере. Все указанное, не являющееся диском iSCSI, используется системой, например для диска ОС.

    ```bash
    sudo vgs
    ```

16. Измените раздел конфигурации активации файла /etc/lvm/lvm.conf. Настройте следующую строку.

    ```bash
    volume_list = [ <ListOfVGsNotUsedByPacemaker> ]
    ```

    \<ListOfVGsNotUsedByPacemaker> — это список групп томов из выходных данных шага 20, которые не будут использоваться экземпляром отказоустойчивого кластера. Заключите каждый из них в кавычки и разделите запятыми. Ниже приведен пример такого файла.

    ![55-ListOfVGs][11]
 
 
17. При запуске Linux подключит файловую систему. Чтобы убедиться, что только Pacemaker может подключить диск iSCSI, перестройте корневой образ файловой системы. 

    Выполните приведенную ниже команду, что может занять несколько секунд. При успешном выполнении команда не возвращает никакие сообщение.

    ```bash
    sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r)
    ```

18. Перезагрузите сервер.

19. На другом сервере, который будет участвовать в экземпляре отказоустойчивого кластера, выполните шаги 1–6. В результате цель iSCSI будет представлена для SQL Server. 
 
20. Создайте список групп томов на сервере. В нем должна отображаться созданная ранее группа томов. 

    ```bash
    sudo vgs
    ``` 
23. Запустите SQL Server и убедитесь, что он может быть запущен на этом сервере.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```

24. Остановите сервер SQL Server и убедитесь в том, что его работа прекращена.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
25. Повторите шаги 1–6 на всех других серверах, которые будут участвовать в экземпляре отказоустойчивого кластера.

Теперь вы готовы к настройке экземпляра отказоустойчивого кластера.

|Distribution |Раздел 
|----- |-----
|**Red Hat Enterprise Linux с надстройкой высокой доступности (HA)** |[Настройка](sql-server-linux-shared-disk-cluster-configure.md)<br/>[Эксплуатация](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server с надстройкой высокой доступности (HA)** |[Настройка](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>Дальнейшие действия

[Настройка экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/05-initiator.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/10-iscsiTargetSettings.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/15-iSCSITargetResults.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/20-iSCSITargetLogin.png
[5]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/25-iSCSIVerify.png
[6]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/7-setiscsinetwork.png
[7]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/30-iSCSIattachedDisks.png
[8]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/45-CopyMove.png
[9]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/50-ExampleCreateSSMS.png
[10]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/40-Create25GBVol.png
[11]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/55-ListOfVGs.png

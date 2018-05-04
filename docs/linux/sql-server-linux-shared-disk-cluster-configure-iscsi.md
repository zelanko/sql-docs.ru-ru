---
title: Настройка отказоустойчивого кластера экземпляра хранилища iSCSI - SQL Server для Linux | Документы Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.openlocfilehash: d3b1fa90c6112247c88b9e148bc65c0cef7be0b0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="configure-failover-cluster-instance---iscsi---sql-server-on-linux"></a>Настройка экземпляра отказоустойчивого кластера — iSCSI - SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка хранения iSCSI для экземпляра отказоустойчивого кластера (FCI) в Linux. 

## <a name="configure-iscsi"></a>Настройка iSCSI 
с помощью сети iSCSI представляет диски с сервера, известный как целевой объект, к серверам. Подключение к цели iSCSI требуют настроен, инициатор iSCSI. Диски на целевом сервере получают явные разрешения, чтобы только инициаторы, должны иметь возможность доступа к ним можно сделать это. Целевой объект сам должен быть высоким уровнем доступности и надежности.

### <a name="important-iscsi-target-information"></a>Целевые сведения о важных iSCSI
Хотя в этом разделе будет рассматривается настройка цели iSCSI, так как это зависящее от типа источника, который планируется использовать, убедитесь, что настроено безопасности для дисков, которые будут использоваться узлами кластера.  

Целевой объект никогда не должны быть настроены на любом из узлов отказоустойчивого Кластера, если использование цели iSCSI под управлением Linux. Для обеспечения производительности и доступности сети iSCSI необходимо отделить от используемых регулярных сетевого трафика на исходном и с клиентскими серверами. Должен быть быстрым, сеть, используемая для iSCSI. Помните, использование некоторых процессоров пропускной способности, поэтому распланировать при использовании обычных сервера этой сети.
Является наиболее важным для обеспечения выполнено на целевом сервере — что диски, которые создаются назначены соответствующие разрешения, так что только серверы, участвующие в FCI имеют доступ к ним. Ниже показан пример цели iSCSI Microsoft, где linuxnodes1 — это имя, созданное, а в этом случае IP-адреса узлов, назначенных для отображения NewFCIDisk1.vhdx к ним.

![Инициатор][1]

### <a name="instructions"></a>Instructions

В этом разделе рассматривается настройка инициатора iSCSI на серверах, которые будут служить узлами для FCI. Инструкции должны работать на RHEL и Ubuntu.

Дополнительные сведения о инициатора iSCSI для поддерживаемых дистрибутивах можно найти по следующим ссылкам:
- [Red Hat](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/iscsi-api.html)
- [SUSE](http://www.suse.com/documentation/sles11/stor_admin/data/sec_inst_system_iscsi_initiator.html) 
- [Ubuntu](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

1.  Выберите один из серверов, которые будут участвовать в конфигурации отказоустойчивого Кластера. Неважно, какой из них. должно быть iSCSI на выделенную сеть, поэтому настройте iSCSI распознавать и использовать эту сеть. Запустите `sudo iscsiadm -m iface -I <iSCSIIfaceName> -o new` где `<iSCSIIfaceName>` уникальный или понятное имя для сети. В следующем примере используется `iSCSINIC`:
   
    ```bash
    sudo iscsiadm -m iface -I iSCSINIC -o new
    ```
    ![7-setiscsinetwork][6]
 
2.  Изменить `/var/lib/iscsi/ifaces/iSCSIIfaceName`. Убедитесь, что он имеет полностью заполнить следующие значения:

    - iface.net_ifacename — это имя сетевого адаптера, как показано в операционной системе.
    - iface.hwaddress является MAC-адрес уникальное имя, которое будет создаваться для этого интерфейса ниже.
    - iface.IPAddress
    - iface.subnet_Mask 

    См. следующий пример.

    ![iSCSITargetSettings][2]

3.  Найти цели iSCSI.

    ```bash
    sudo iscsiadm -m discovery -t sendtargets -I <iSCSINetName> -p <TargetIPAddress>:<TargetPort>
    ```

     \<iSCSINetName > — это уникальное и понятное имя для сети, \<TargetIPAddress > IP-адрес цели iSCSI, и \<TargetPort > — это порт цели iSCSI. 

    ![iSCSITargetResults][3]

 
4.  Войдите на целевой объект

    ```bash
    sudo iscsiadm -m node -I <iSCSIIfaceName> -p TargetIPAddress -l
    ```

    \<iSCSIIfaceName > — это уникальное и понятное имя для сети и \<TargetIPAddress > IP-адрес, конечный объект iSCSI.

    ![iSCSITargetLogin][4]

5.  Проверьте, что имеется подключение к цели iSCSI.

    ```bash
    sudo iscsiadm -m session
    ```

    ![iSCSIVerify][5]

 
6.  Проверьте подключенными дисками iSCSI

    ```bash
    sudo grep “Attached SCSI” /var/log/messages
    ```
    ![30 iSCSIattachedDisks][7]

7.  Создание физического тома на диске iSCSI.

    ```bash
    sudo pvcreate /dev/<devicename>
    ```

    \<DeviceName > — имя устройства из предыдущего шага. 

 
8.  Создание группы томов на диске iSCSI. Диски, назначенные в одну группу томов представляются в пул или коллекцию. 

    ```bash
    sudo vgcreate <VolumeGroupName> /dev/devicename
    ```

    \<VolumeGroupName > — имя группы томов и \<devicename > — имя устройства в шаге 6. 
 
9.  Создание и проверка логического тома для диска.

    ```bash
    sudo lvcreate -Lsize -n <LogicalVolumeName> <VolumeGroupName>
    ```
    
    \<размер > — это размер тома, чтобы создать и может быть указан с G (в гигабайтах), T (терабайт), т. д.,\<LogicalVolumeName > — имя логического тома и \<VolumeGroupName > — имя группы томов из предыдущий шаг. 

    В приведенном ниже примере создает том 25 ГБ.
 
    ![Create25GBVol][10]

10. Выполнение `sudo lvs` для просмотра LVM, который был создан.
 
11. Формате логический том с поддерживаемой файловой системы. Для EXT4 используйте следующий пример:

    ```bash
    sudo mkfs.ext4 /dev/<VolumeGroupName>/<LogicalVolumeName>
    ```

    \<VolumeGroupName > — имя группы томов из предыдущего шага. \<LogicalVolumeName > — имя логического тома из предыдущего шага.  

12. Для системных баз данных или все данные, хранящиеся в расположении данных по умолчанию выполните следующие действия. В противном случае перейдите к шагу 13.

   *    Убедитесь, что SQL Server остановлена на сервере, вы работаете.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Переключитесь в полностью быть суперпользователем. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    sudo -i
    ```

   *    Переключатель — mssql пользователя. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    su mssql
    ```

   *    Создайте временный каталог для хранения данных SQL Server и файлы журнала. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > — имя папки. В приведенном ниже примере создается папка с именем /var/opt/mssql/TempDir.

    ```bash
    mkdir /var/opt/mssql/TempDir
    ```
    
   *    Скопируйте файлы данных и журналов SQL Server во временный каталог. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > — имя папки из предыдущего шага.
    
   *    Убедитесь, что файлы находятся в каталоге.

    ```bash
    ls \<TempDir>
    ```
    \<TempDir > — имя каталога, от шагу d.

   *    Удалите файлы из существующего каталога данных SQL Server. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   *    Убедитесь, что файлы были удалены. На рисунке ниже показан пример вся последовательность от c до h.

    ```bash
    ls /var/opt/mssql/data
    ```

    ![45 CopyMove][8]
 
   *    Тип `exit` переключение обратно на привилегированного пользователя.

   *    Подключите iSCSI логический том в папке данных SQL Server. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> /var/opt/mssql/data
    ``` 

    \<VolumeGroupName > — имя группы томов и \<LogicalVolumeName > — имя логического тома, который был создан. Следующий пример синтаксиса соответствующие группы томов и логического тома из предыдущей команды.

    ```bash
    mount /dev/FCIDataVG1/FCIDataLV1 /var/opt/mssql/data
    ``` 

   *    Смените владельца подключения mssql. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    chown mssql /var/opt/mssql/data
    ```

   *    Изменить владельца группы подключения для mssql. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    chgrp mssql /var/opt/mssql/data
    ``` 

   *    Переключитесь в mssql пользователя. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    su mssql
    ``` 

   *    Скопируйте файлы из /var/opt/mssql/data временный каталог. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    cp /var/opt/mssql/TempDir/* /var/opt/mssql/data
    ``` 

   *    Убедитесь, что файлы существуют.

    ```bash
    ls /var/opt/mssql/data
    ``` 
 
   *    Введите `exit` не является mssql.
    
   *    Введите `exit` не является корневым.

   *    Запустите SQL Server. Если все, что был правильно скопирован и обеспечения безопасности, SQL Server должен показывать начала работы.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ``` 
 
   *    Остановка SQL Server и убедитесь, что завершение работы.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ``` 

13. Для выполнения задач, кроме системных баз данных пользовательских баз данных или создание резервных копий выполните следующие действия. Если только расположение по умолчанию, перейдите к шагу 14.

   *    Параметр, добавляемый суперпользователя. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    sudo -i
    ```

   *    Создайте папку, которая будет использоваться SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Имя папки > — имя папки. Полный путь к папке должен быть указан не в надлежащем расположении if. В приведенном ниже примере создается папка с именем /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    Подключите логический том iSCSI в папку, созданную на предыдущем шаге. Вы не получите любое подтверждение в случае успешного выполнения.
    
    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > — имя группы томов \<LogicalVolumeName > имя логического тома, который был создан, и \<имя_папки > — имя папки. Ниже приведен пример синтаксиса.

    ```bash
    mount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

   *    Изменить владельца для mssql созданной папки. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    chown mssql <FolderName>
    ```

    \<Имя папки > — имя папки, которая была создана. Пример показан ниже.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```
  
   *    Измените группу для mssql созданной папки. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    chown mssql <FolderName>
    ```

    \<Имя папки > — имя папки, которая была создана. Пример показан ниже.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```

   *    Тип `exit` больше не суперпользователя.

   *    Чтобы проверить, создайте базу данных в этой папке. Пример, приведенный ниже использует sqlcmd для создания базы данных, переходить в контекст, проверьте файлы существуют на уровне операционной системы, а затем удаляет временное расположение. Можно использовать среду SSMS.
  
    ![50 ExampleCreateSSMS][9]

   *    Отключение общего ресурса 

    ```bash
    sudo umount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > — имя группы томов \<LogicalVolumeName > имя логического тома, который был создан, и \<имя_папки > — имя папки. Ниже приведен пример синтаксиса.

    ```bash
    sudo umount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

14. Настройте сервер, так что только Pacemaker можно активировать группы томов.

    ```bash
    sudo lvmconf --enable-halvm --services –startstopservices
    ```
 
15. Создайте список групп томов на сервере. Все компоненты в списке, не диск iSCSI используется системой, такие как для диска операционной системы.

    ```bash
    sudo vgs
    ```

16. Измените раздел конфигурации активации /etc/lvm/lvm.conf файла. Настройте следующую строку:

    ```bash
    volume_list = [ <ListOfVGsNotUsedByPacemaker> ]
    ```

    \<ListOfVGsNotUsedByPacemaker > — список групп томов из выходных данных шага 20, не будет использоваться FCI. Поместите каждый из них в кавычки и отдельные с помощью символа запятой. Пример показан ниже.

    ![55 ListOfVGs][11]
 
 
17. При запуске Linux, он будет подключения файловой системы. Чтобы убедиться, что только Pacemaker можно подключить диск iSCSI, перестройте изображение корневой файловой системы. 

    Запустите следующую команду, которая может занять несколько минут для завершения. Вы получите сообщение не обратно в случае успешного выполнения.

    ```bash
    sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r)
    ```

18. Перезагрузите сервер.

19. На другом сервере, который будет участвовать в отказоустойчивом кластере выполните шаги 1 – 6. При этом возникнет цели iSCSI к SQL Server. 
 
20. Создайте список групп томов на сервере. Должна отобразиться группы томов, созданного ранее. 

    ```bash
    sudo vgs
    ``` 
23. Запуск SQL Server и убедитесь, что его можно запустить на этом сервере.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```

24. Остановка SQL Server и убедитесь, что она завершена.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
25. Повторите шаги 1 – 6 на других серверах, которые будут участвовать в отказоустойчивом кластере.

Теперь вы готовы к настройке FCI.

|Distribution |Раздел 
|----- |-----
|**Red Hat Enterprise Linux с надстройками высокого уровня ДОСТУПНОСТИ** |[Настройка](sql-server-linux-shared-disk-cluster-configure.md)<br/>[Эксплуатация](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server с дополнительным высокого уровня ДОСТУПНОСТИ** |[Настройка](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>Следующие шаги

[Настроить экземпляр отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure.md)

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

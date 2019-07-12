---
title: Настройка отказоустойчивого кластера экземпляра хранилища iSCSI - SQL Server в Linux
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 89a72a7390b3b782781c4849d69f81065544e991
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833191"
---
# <a name="configure-failover-cluster-instance---iscsi---sql-server-on-linux"></a>Настройка экземпляра отказоустойчивого кластера — iSCSI — SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка хранилища iSCSI для экземпляра отказоустойчивого кластера (FCI) в Linux. 

## <a name="configure-iscsi"></a>Настройка iSCSI 
с помощью сети iSCSI представляет диски с сервера, известный как целевой объект, к серверам. Серверы, подключение к целевому объекту iSCSI требуют, что настроена инициатор iSCSI. Таким образом, чтобы только инициаторы, которым требуется разрешение на доступ к ним можно сделать это, диски на целевом объекте получают явные разрешения. Целью самого должна быть высокой доступностью и надежностью.

### <a name="important-iscsi-target-information"></a>Целевые сведения о важных iSCSI
Хотя в этом разделе не рассматривается настройка цели iSCSI, так как это от типа источника, который вы будете использовать, убедитесь, что настройки параметров безопасности для дисков, которые будут использоваться узлами кластера.  

Целевой объект никогда не должен быть настроен на всех узлах отказоустойчивого Кластера, если использование цели iSCSI под управлением Linux. Производительность и доступность необходимо отделить от используемых обычного сетевого трафика на исходном, так и с клиентскими серверами сети iSCSI. Сетей, используемых для iSCSI должна работать быстро. Помните, этой сети используют некоторые пропускной способности процессора, поэтому планируйте сеансы при использовании обычный сервер.
Наиболее важно обеспечить выполнено на целевом объекте — что диски, которые создаются назначены соответствующие разрешения, таким образом, чтобы только серверы, входящие в FCI имеют к ним доступ. Ниже приведен пример из целевого объекта iSCSI Microsoft, где linuxnodes1 это имя, созданное и таким образом, IP-адреса узлов назначаются для отображения NewFCIDisk1.vhdx к ним.

![Инициатор][1]

### <a name="instructions"></a>Instructions

В этом разделе мы рассмотрим, как настроить инициатор iSCSI на серверах, которые будут работать в качестве узлов отказоустойчивого Кластера. Инструкции должны работать как есть в RHEL и Ubuntu.

Дополнительные сведения о инициатора iSCSI для поддерживаемых дистрибутивов можно найти по следующим ссылкам:
- [Red Hat](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/iscsi-api.html)
- [SUSE](https://www.suse.com/documentation/sles11/stor_admin/data/sec_inst_system_iscsi_initiator.html) 
- [Ubuntu](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

1.  Выберите один из серверов, которые будут участвовать в конфигурации отказоустойчивого Кластера. Неважно, какой из них. должно быть iSCSI на выделенную сеть, поэтому настройте iSCSI для распознавания и использования этой сети. Запустите `sudo iscsiadm -m iface -I <iSCSIIfaceName> -o new` где `<iSCSIIfaceName>` уникальный или понятное имя для сети. В следующем примере используется `iSCSINIC`:
   
    ```bash
    sudo iscsiadm -m iface -I iSCSINIC -o new
    ```
    ![7-setiscsinetwork][6]
 
2.  Изменить `/var/lib/iscsi/ifaces/iSCSIIfaceName`. Убедитесь, что он имеет следующие значения, полностью заполнения:

    - iface.net_ifacename — имя сетевой карты, как показано в операционной системе.
    - iface.hwaddress указан MAC-адрес из уникального имени, который будет создан для этого интерфейса ниже.
    - iface.ipaddress
    - iface.subnet_Mask 

    См. следующий пример.

    ![iSCSITargetSettings][2]

3.  Найти целевой объект iSCSI.

    ```bash
    sudo iscsiadm -m discovery -t sendtargets -I <iSCSINetName> -p <TargetIPAddress>:<TargetPort>
    ```

     \<iSCSINetName > — это уникальное и понятное имя для сети, \<TargetIPAddress > является IP-адрес целевой объект iSCSI, и \<TargetPort > — это порт цели iSCSI. 

    ![iSCSITargetResults][3]

 
4.  Войдите на целевой объект

    ```bash
    sudo iscsiadm -m node -I <iSCSIIfaceName> -p TargetIPAddress -l
    ```

    \<iSCSIIfaceName > — это уникальное и понятное имя для сети и \<TargetIPAddress > является IP-адрес целевой объект iSCSI.

    ![iSCSITargetLogin][4]

5.  Установите этот флажок, чтобы проверить, что подключение к целевому объекту iSCSI.

    ```bash
    sudo iscsiadm -m session
    ```

    ![iSCSIVerify][5]

 
6.  Проверьте присоединенных дисков iSCSI

    ```bash
    sudo grep "Attached SCSI" /var/log/messages
    ```
    ![30-iSCSIattachedDisks][7]

7.  Создайте физические тома на диск iSCSI.

    ```bash
    sudo pvcreate /dev/<devicename>
    ```

    \<DeviceName > — имя устройства из предыдущего шага. 

 
8.  Создание группы томов на диск iSCSI. Диски, назначенные в одну группу томов, видны как пула или коллекции. 

    ```bash
    sudo vgcreate <VolumeGroupName> /dev/devicename
    ```

    \<VolumeGroupName > — имя группы томов и \<devicename > — имя устройства из шага 6. 
 
9.  Создание и проверка логического тома для диска.

    ```bash
    sudo lvcreate -Lsize -n <LogicalVolumeName> <VolumeGroupName>
    ```
    
    \<размер > — это размер тома, который требуется создать и может быть указан с помощью G (гигабайт), T (терабайты), и т.д.,\<LogicalVolumeName > — это имя логического тома, и \<VolumeGroupName > — имя группы томов из предыдущий шаг. 

    В приведенном ниже примере создает том 25 ГБ.
 
    ![Create25GBVol][10]

10. Выполнение `sudo lvs` для см. в разделе диспетчера логических ТОМОВ, который был создан.
 
11. Измените формат логического тома с поддерживаемой файловой системы. Для EXT4 используйте следующий пример:

    ```bash
    sudo mkfs.ext4 /dev/<VolumeGroupName>/<LogicalVolumeName>
    ```

    \<VolumeGroupName > — имя группы томов из предыдущего шага. \<LogicalVolumeName > — это имя логического тома из предыдущего шага.  

12. Для системных баз данных или все данные, хранящиеся в расположении данных по умолчанию выполните следующие действия. В противном случае перейдите к шагу 13.

   *    Убедитесь, что SQL Server остановлена на сервере, которым вы работаете.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Переключиться в режим полностью стать суперпользователем. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    sudo -i
    ```

   *    Ключ пользователя mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    su mssql
    ```

   *    Создайте временный каталог для хранения данных SQL Server и файлов журнала. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > — это имя папки. В приведенном ниже примере создает папку с именем /var/opt/mssql/TempDir.

    ```bash
    mkdir /var/opt/mssql/TempDir
    ```
    
   *    Скопируйте файлы данных и журналов SQL Server во временный каталог. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > — это имя папки, из предыдущего шага.
    
   *    Убедитесь, что файлы находятся в каталоге.

    ```bash
    ls \<TempDir>
    ```
    \<TempDir > — это имя папки из шагу d.

   *    Удалите файлы из существующего каталога данных SQL Server. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   *    Убедитесь, что файлы были удалены. На рисунке ниже показан пример всей последовательности из c помощью h.

    ```bash
    ls /var/opt/mssql/data
    ```

    ![45-CopyMove][8]
 
   *    Тип `exit` переключиться обратно на привилегированного пользователя.

   *    Подключите iSCSI логический том в папке данных SQL Server. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> /var/opt/mssql/data
    ``` 

    \<VolumeGroupName > — имя группы томов и \<LogicalVolumeName > — это имя логического тома, который был создан. Следующий пример синтаксиса соответствующий группы томов и логическими томами из предыдущей команды.

    ```bash
    mount /dev/FCIDataVG1/FCIDataLV1 /var/opt/mssql/data
    ``` 

   *    Изменения владельца диска на mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    chown mssql /var/opt/mssql/data
    ```

   *    Изменить владельца группы подключения для mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    chgrp mssql /var/opt/mssql/data
    ``` 

   *    Переключитесь на пользователя mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    su mssql
    ``` 

   *    Скопируйте файлы из /var/opt/mssql/data во временный каталог. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    cp /var/opt/mssql/TempDir/* /var/opt/mssql/data
    ``` 

   *    Убедитесь, что файлы существуют.

    ```bash
    ls /var/opt/mssql/data
    ``` 
 
   *    Введите `exit` не является mssql.
    
   *    Введите `exit` не является корневой.

   *    Запустите SQL Server. Если все, что был скопирован правильно, и обеспечения безопасности, SQL Server должна отобразиться как к работе.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ``` 
 
   *    Остановка SQL Server и убедитесь, что завершение работы.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ``` 

13. Для таких вещей, кроме системных баз данных, таких как пользовательских баз данных или резервных копий выполните следующие действия. Если только с использованием расположения по умолчанию, перейдите к шагу 14.

   *    Переключатель, чтобы стать суперпользователем. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    sudo -i
    ```

   *    Создайте папку, которая будет использоваться SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Имя папки > — это имя папки. Полный путь к папке должен быть указан не в надлежащем расположении if. В приведенном ниже примере создает папку с именем /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    Подключите iSCSI логический том в папке, который был создан на предыдущем шаге. Вы не получите любое подтверждение при успешном выполнении.
    
    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > — имя группы томов, \<LogicalVolumeName > — это имя логического тома, который был создан, и \<имя_папки > — это имя папки. Ниже приведен пример синтаксиса.

    ```bash
    mount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

   *    Изменить владельца папки, созданной для mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    chown mssql <FolderName>
    ```

    \<Имя папки > — имя папки, которая была создана. Пример показан ниже.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```
  
   *    Измените группу для папки, созданной для mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    chown mssql <FolderName>
    ```

    \<Имя папки > — имя папки, которая была создана. Пример показан ниже.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```

   *    Тип `exit` больше не суперпользователь.

   *    Чтобы проверить, создайте базу данных в этой папке. Приведенном ниже примере использует sqlcmd для создания базы данных, переключить контекст на него, проверьте файлы существуют на уровне операционной системы, а затем удаляет во временную папку. Можно использовать SSMS.
  
    ![50-ExampleCreateSSMS][9]

   *    Отключить общую папку 

    ```bash
    sudo umount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > — имя группы томов, \<LogicalVolumeName > — это имя логического тома, который был создан, и \<имя_папки > — это имя папки. Ниже приведен пример синтаксиса.

    ```bash
    sudo umount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

14. Настройте сервер, чтобы этот единственный Pacemaker может активировать группу томов.

    ```bash
    sudo lvmconf --enable-halvm --services -startstopservices
    ```
 
15. Создайте список групп томов на сервере. Все компоненты в списке, не диск iSCSI используется системой, такие как для диска ОС.

    ```bash
    sudo vgs
    ```

16. Измените раздел конфигурации активации из файла /etc/lvm/lvm.conf. Настройте следующую строку:

    ```bash
    volume_list = [ <ListOfVGsNotUsedByPacemaker> ]
    ```

    \<ListOfVGsNotUsedByPacemaker > — это список групп томов из выходных данных 20 шаг, который не будет использоваться экземпляром отказоустойчивого Кластера. Поместите каждый из них, в кавычках и отдельные с помощью символа запятой. Пример показан ниже.

    ![55 ListOfVGs][11]
 
 
17. При запуске Linux, он будет подключения файловой системы. Чтобы убедиться, что только Pacemaker можно было подключить диск iSCSI, перестройка образа корневой файловой системы. 

    Выполните следующую команду, которая может занять несколько секунд. Вы получите сообщение не обратно при успешном выполнении.

    ```bash
    sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r)
    ```

18. Перезагрузите сервер.

19. На другом сервере, который будет участвовать в FCI выполните шаги 1 - 6. При этом возникнет целевому объекту iSCSI к SQL Server. 
 
20. Создайте список групп томов на сервере. Она должна отобразиться в группу томов, созданные ранее. 

    ```bash
    sudo vgs
    ``` 
23. Запуск SQL Server и убедитесь, что его можно запустить на этом сервере.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```

24. Остановка SQL Server и убедитесь, что она была завершена.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
25. Повторите шаги 1 – 6 на других серверах, которые будут участвовать в FCI.

Теперь вы готовы к настройке экземпляра отказоустойчивого Кластера.

|Distribution |Раздел 
|----- |-----
|**Red Hat Enterprise Linux с надстройкой с высоким уровнем ДОСТУПНОСТИ** |[Настройка](sql-server-linux-shared-disk-cluster-configure.md)<br/>[Эксплуатация](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server с надстройкой с высоким уровнем ДОСТУПНОСТИ** |[Настройка](sql-server-linux-shared-disk-cluster-sles-configure.md)

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

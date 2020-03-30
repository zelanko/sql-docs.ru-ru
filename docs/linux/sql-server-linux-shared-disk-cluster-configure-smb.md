---
title: Настройка экземпляра отказоустойчивого кластера хранилища SMB — SQL Server на Linux
description: Узнайте, как настроить экземпляр отказоустойчивого кластера с помощью хранилища SMB для SQL Server на Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 498518fbc119629d2e7da7717b1f6e41c68984ce
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75558587"
---
# <a name="configure-failover-cluster-instance---smb---sql-server-on-linux"></a>Настройка экземпляра отказоустойчивого кластера (SMB) — SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается, как настроить хранилище SMB для экземпляра отказоустойчивого кластера в Linux. 
 
За пределами Windows SMB часто называется общим ресурсом Common Internet File System (CIFS) и реализуется посредством Samba. В Windows доступ к общему ресурсу SMB осуществляется следующим образом. \\имя_сервера\имя_общего_ресурса\. При установке SQL Server в Linux общий ресурс SMB должен быть подключен в качестве папки.

## <a name="important-source-and-server-information"></a>Важные сведения об источнике и сервере

Ниже приведены некоторые советы и замечания по успешному использованию SMB.
- Общий ресурс SMB может находиться в Windows, Linux или даже на устройстве, если используется SMB 3.0 или более поздней версии. См. дополнительные сведения о Samba и SMB 3.0 в [описании SMB 3.0](https://wiki.samba.org/index.php/Samba3/SMB2#SMB_3.0), чтобы узнать, соответствует ли ваша реализация Samba требованиям SMB 3.0.
- Общий ресурс SMB должен быть высокодоступным.
- Для общего ресурса SMB должна быть обеспечена надлежащая безопасность. Ниже приведен пример /etc/samba/smb.conf, где SQLData1 — это имя общего ресурса.

![05-smbsource][1]

## <a name="instructions"></a>Instructions

1. Выберите один из серверов, которые будут включены в конфигурацию экземпляра отказоустойчивого кластера. Какой именно — не имеет значения.
   
1. Получите сведения о пользователе mssql.
   
   ```bash
    sudo id mssql
   ```
   
   Обратите внимание на значения uid, gid и groups. 
   
1. Выполните процедуру `sudo smbclient -L //NameOrIP/ShareName -U User`.
   
   \<NameOrIP> — это DNS-имя или IP-адрес сервера, на котором размещается общий ресурс SMB.
   
   \<ShareName> — это имя общего ресурса SMB. 
   
1. Для системных баз данных или других объектов, хранящихся в расположении данных по умолчанию, выполните указанные ниже действия. В противном случае перейдите к шагу 5. 
   
   1. Убедитесь в том, что SQL Server остановлен на сервере, на котором вы работаете.
      ```bash
      sudo systemctl stop mssql-server
      sudo systemctl status mssql-server
      ```
      
   1. Перейдите в режим суперпользователя. В случае успешного действия подтверждение не выводится.
      
      ```bash
      sudo -i
      ```
      
   1. Переключитесь на пользователя mssql. В случае успешного действия подтверждение не выводится.
      
      ```bash
      su mssql
      ```
      
   1. Создайте временный каталог для хранения данных и файлов журналов SQL Server. В случае успешного действия подтверждение не выводится.
      
      ```bash
      mkdir <TempDir>
      ```
      
      \<TempDir> — это имя папки. В приведенном ниже примере создается папка /var/opt/mssql/tmp.
      
      ```bash
      mkdir /var/opt/mssql/tmp
      ```
      
   1. Скопируйте данные и файлы журналов SQL Server во временный каталог. В случае успешного действия подтверждение не выводится.
      
      ```bash
      cp /var/opt/mssql/data/* <TempDir>
      ```
      
      \<TempDir> — это имя папки из предыдущего шага.
      
   1. Проверьте наличие файлов в папке.
      
      ```bash
      ls <TempDir>
      ```
      
      \<TempDir> — это имя папки из шага d.
      
   1. Удалите файлы из существующего каталога данных SQL Server. В случае успешного действия подтверждение не выводится.
      
      ```bash
      rm - f /var/opt/mssql/data/*
      ```
      
   1. Проверьте, были ли файлы удалены. 
      
      ```bash
      ls /var/opt/mssql/data
      ```
      
   1. Введите exit, чтобы переключиться на привилегированного пользователя.
      
   1. Подключите общий ресурс SMB в папке данных SQL Server. В случае успешного действия подтверждение не выводится. В этом примере показан синтаксис для подключения к общему ресурсу SMB 3.0 на базе Windows Server.
      
      ```bash
      Mount -t cifs //<ServerName>/<ShareName> /var/opt/mssql/data -o vers=3.0,username=<UserName>,password=<Password>,domain=<domain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
      ```
      
      \<ServerName> — это имя сервера с общим ресурсом SMB.
      
      \<ShareName> — это имя общей папки.
      
      \<UserName> — это имя пользователя для доступа к общей папке.
      
      \<Password> — это пароль пользователя.
      
      \<domain> — это имя Active Directory.
      
      \<mssqlUID> — это идентификатор UID пользователя mssql. 
      
      \<mssqlGID> — это идентификатор GID пользователя mssql.
      
   1. Проверьте, было ли подключение выполнено успешно, с помощью команды mount без параметров.
      
      ```bash
      mount
      ```
      
   1. Переключитесь на пользователя mssql. В случае успешного действия подтверждение не выводится.
      
      ```bash
      su mssql
      ```
      
   1. Скопируйте файлы из временного каталога /var/opt/mssql/data. В случае успешного действия подтверждение не выводится.
      
      ```bash
      cp /var/opt/mssql/tmp/* /var/opt/mssql/data
      ```
      
   1. Проверьте наличие файлов.
      
      ```bash
      ls /var/opt/mssql/data
      ```
      
   1. Введите exit, чтобы выйти из учетной записи mssql. 
      
   1. Введите exit, чтобы выйти из учетной записи привилегированного пользователя.
   
   1. Запустите SQL Server. Если все данные были скопированы и параметры безопасности применены правильно, сервер SQL Server должен отобразиться как запущенный.
      
      ```bash
      sudo systemctl start mssql-server
      sudo systemctl status mssql-server
      ```
      
   1. Для дальнейшего тестирования создайте базу данных, чтобы обеспечить правильность разрешений. В следующем примере используется Transact-SQL, но вы можете использовать SSMS.
      
      ![10_testcreatedb][2] 
      
   1. Остановите сервер SQL Server и убедитесь в том, что его работа прекращена. Если вы планируете добавить или протестировать другие диски, не завершайте работу SQL Server, пока они не будут добавлены и протестированы.
      
      ```bash
      sudo systemctl stop mssql-server
      sudo systemctl status mssql-server
      ```
      
   1. Отключите общую папку, только если выполнены все задачи. В противном случае отключите общую папку после завершения тестирования или добавления дополнительных дисков.
      
      ```bash
      sudo umount //<IPAddressorServerName>/<ShareName /<FolderMountedIn>
      ```
      
      \<IPAddressOrServerName> — это IP-адрес или имя узла SMB.
      
      \<ShareName> — это имя общей папки.
      
      \<FolderMountedIn> — это имя папки, где подключен SMB.
      
5. Для объектов, отличных от системных баз данных, например пользовательских баз данных или резервных копий, выполните указанные ниже действия. Если используется только расположение по умолчанию, перейдите к шагу 14.
   
   1. Перейдите в режим суперпользователя. В случае успешного действия подтверждение не выводится.
      
      ```bash
      sudo -i
      ```
      
   1. Создайте папку, которая будет использоваться сервером SQL Server. 
      
      ```bash
      mkdir <FolderName>
      ```
      
      \<FolderName> — это имя папки. Если папка находится в другом месте, необходимо указать полный путь к ней. В приведенном ниже примере создается папка /var/opt/mssql/userdata.
      
      ```bash
      mkdir /var/opt/mssql/userdata
      ```
      
   1. Подключите общий ресурс SMB в папке данных SQL Server. В случае успешного действия подтверждение не выводится. В этом примере показан синтаксис для подключения к общему ресурсу SMB 3.0 на базе Samba.
      
      ```bash
      Mount -t cifs //<ServerName>/<ShareName> <FolderName> -o vers=3.0,username=<UserName>,password=<Password>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
      ```
      
      \<ServerName> — это имя сервера с общим ресурсом SMB.
      
      \<ShareName> — это имя общей папки.
      
      \<FolderName> — имя папки, созданной на последнем шаге.  
      
      \<UserName> — это имя пользователя для доступа к общей папке.
      
      \<Password> — это пароль пользователя.
      
      \<mssqlUID> — это идентификатор UID пользователя mssql.
      
      \<mssqlGID> — это идентификатор GID пользователя user.
      
   1. Проверьте, было ли подключение выполнено успешно, с помощью команды mount без параметров.
   
   1. Введите exit, чтобы выйти из режима суперпользователя.
   
   1. Создайте в этой папке базу данных для тестирования. В приведенном ниже примере создается база данных с помощью sqlcmd, переключается контекст, проверяется наличие файлов на уровне ОС, а затем временная папка удаляется. Можно также использовать SSMS.
   
   1. Отключение общей папки 
      
      ```bash
      sudo umount //<IPAddressorServerName>/<ShareName> /<FolderMountedIn>
      ```
      
      \<IPAddressOrServerName> — это IP-адрес или имя узла SMB.
      
      \<ShareName> — это имя общей папки.
      
      \<FolderMountedIn> — это имя папки, где подключен SMB.
   
1. Повторите эти действия на других узлах.

Теперь вы готовы к настройке экземпляра отказоустойчивого кластера.

## <a name="next-steps"></a>Дальнейшие действия

[Настройка экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/05-smbsource.png 
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/10-testcreatedb.png 

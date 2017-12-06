---
title: "Настройка отказоустойчивого кластера экземпляра хранилища SMB - SQL Server для Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 8043cd57758749399500b206410694c1735b30e8
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="configure-failover-cluster-instance---smb---sql-server-on-linux"></a>Настройте экземпляр отказоустойчивого кластера — SMB - SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этой статье объясняется, как настроить хранилище SMB для экземпляра отказоустойчивого кластера (FCI) в Linux. 
 
В мире не под управлением Windows часто называют совместно использовать как общие файловая система Интернета (CIFS) и реализуются с помощью Samba SMB. В системе Windows доступ к общей папке SMB выполняется таким образом: \\имя_сервера\имя_общего_ресурса. Для установки SQL Server под управлением Linux в общей папке SMB, необходимо подключить как папка.

## <a name="important-source-and-server-information"></a>Важные сведения об источнике и сервере

Ниже приведены некоторые советы и примечания для успешного использования SMB.
- В общей папке SMB может быть на Windows, Linux, а также с управляющим устройством, как долго, как она использует SMB 3.0 или более поздней версии. Дополнительные сведения о Samba и SMB 3.0 см. в разделе [SMB 3.0](https://wiki.samba.org/index.php/Samba3/SMB2#SMB_3.0) ли реализация Samba совместимых с SMB 3.0.
- В общей папке SMB следует иметь высокую доступность.
- Необходимо выполнить настройку безопасности должным образом в общей папке SMB. Ниже приведен пример из /etc/samba/smb.conf, где SQLData1 — это имя общего ресурса.

![05 smbsource][1]

## <a name="instructions"></a>Instructions

1.  Выберите один из серверов, которые будут участвовать в конфигурации отказоустойчивого Кластера. Неважно, какой из них.

2.  Получение сведений о пользователе mssql.

    ```bash
    sudo id mssql
    ```
    
    Обратите внимание, uid, gid и групп. 

3. Выполните процедуру `sudo smbclient -L //NameOrIP/ShareName -U User`.

    \<NameOrIP > DNS-имя или IP-адрес сервера, где размещается в общей папке SMB.

    \<ShareName > — имя общей папки SMB. 

4. Для системных баз данных или все данные, хранящиеся в расположении данных по умолчанию выполните следующие действия. В противном случае перейдите к шагу 5. 

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

    <TempDir>— Это имя папки. В приведенном ниже примере создается папка с именем /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   *    Скопируйте файлы данных и журналов SQL Server во временный каталог. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > — имя папки из предыдущего шага.
    
   *    Убедитесь, что файлы находятся в каталоге.

    ```bash
    ls <TempDir>
    ```

    \<TempDir > — имя каталога, от шагу d.
    
   *    Удалите файлы из существующего каталога данных SQL Server. Вы не получите любое подтверждение в случае успешного выполнения.
 
    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   *    Убедитесь, что файлы были удалены. 

    ```bash
    ls /var/opt/mssql/data
    ```
 
   *    Наберите exit, чтобы вернуться к привилегированного пользователя.

   *    Подключите общей папки SMB в папке данных SQL Server. Вы не получите любое подтверждение в случае успешного выполнения. В этом примере показан синтаксис для подключения к общей папке SMB 3.0 под управлением Windows Server.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> /var/opt/mssql/data -o vers=3.0,username=<UserName>,password=<Password>,domain=<domain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<Имя_сервера > — имя сервера с общей папкой SMB
    
    \<ShareName > — имя общей папки

    \<Имя пользователя > — имя пользователя для доступа к общей папке

    \<Пароль > пароль для пользователя

    \<домен > — имя Active Directory

    \<mssqlUID > имеет уникальный идентификатор пользователя mssql 
 
    \<mssqlGID > является GID mssql пользователя
 
   *    Проверьте подключения прошла успешно, выполнив подключения без ключей.

    ```bash
    mount
    ```
 
   *    Переключитесь в mssql пользователя. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    su mssql
    ```

   *    Скопируйте файлы из /var/opt/mssql/data временный каталог. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssql/data
    ```

   *    Убедитесь, что файлы существуют.

    ```bash
    ls /var/opt/mssql/data
    ```

   *    Введите exit не является mssql 

   *    Введите exit не является корневой

   *    Запустите SQL Server. Если все, что был правильно скопирован и обеспечения безопасности, SQL Server должен показывать начала работы.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
 
   *    Для дальнейшей проверки, создайте базу данных, чтобы убедиться, что разрешения допустимы. В следующем примере используется Transact-SQL; можно использовать среду SSMS.

    ![10_testcreatedb][2] 
  
   *    Остановка SQL Server и убедитесь, что завершение работы. Если планируется добавление или тестирование на других дисках, не завершить работу SQL Server до тех, которые добавляются и протестированы.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Только в том случае, если завершено, отключите общую папку. Если нет, отключить после завершения тестирования и добавления дополнительные диски.

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName /<FolderMountedIn>
    ```

    \<IPAddressOrServerName > — это IP-адрес или имя узла SMB

    \<ShareName > — имя общей папки
    
    \<FolderMountedIn > — имя папки, куда подключен SMB

5.  Для выполнения задач, кроме системных баз данных пользовательских баз данных или создание резервных копий выполните следующие действия. Если только расположение по умолчанию, перейдите к шагу 14.
    
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

   *    Подключите общей папки SMB в папке данных SQL Server. Вы не получите любое подтверждение в случае успешного выполнения. В этом примере показан синтаксис для подключения к общему ресурсу на основе Samba SMB 3.0.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> <FolderName> -o vers=3.0,username=<UserName>,password=<Password>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<Имя_сервера > — имя сервера с общей папкой SMB

    \<ShareName > — имя общей папки

    \<Имя папки > — имя папки, созданные на предыдущем шаге  

    \<Имя пользователя > — имя пользователя для доступа к общей папке

    \<Пароль > пароль для пользователя

    \<mssqlUID > имеет уникальный идентификатор пользователя mssql

    \<mssqlGID > является GID пользователя mssql.
 
   * Проверьте подключения прошла успешно, выполнив подключения без ключей.
 
   * Введите exit для перестанет быть суперпользователем.

   * Чтобы проверить, создайте базу данных в этой папке. Пример, приведенный ниже использует sqlcmd для создания базы данных, переходить в контекст, проверьте файлы существуют на уровне операционной системы, а затем удаляет временное расположение. Можно использовать среду SSMS.
 
   * Отключение общего ресурса 

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName> /<FolderMountedIn>
    ```
    
    \<IPAddressOrServerName > — это IP-адрес или имя узла SMB
 
    \<ShareName > — имя общей папки
 
    \<FolderMountedIn > — имя папки, куда подключен SMB.
 
6.  Повторите шаги на другие узлы.

Теперь вы готовы к настройке FCI.

## <a name="next-steps"></a>Следующие шаги

[Настроить экземпляр отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/05-smbsource.png 
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/10-testcreatedb.png 

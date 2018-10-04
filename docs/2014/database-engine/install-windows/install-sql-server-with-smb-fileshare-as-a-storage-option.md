---
title: Установка SQL Server с общей папкой SMB в качестве хранилища | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 8b7810b2-637e-46a3-9fe1-d055898ba639
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 481a75c420ece410f4b7489013c6297dc7b84869
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211284"
---
# <a name="install-sql-server-with-smb-fileshare-as-a-storage-option"></a>Установка SQL Server с общей папкой SMB в качестве хранилища
  Запуск [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], системные базы данных (Master, Model, MSDB и TempDB), и [!INCLUDE[ssDE](../../includes/ssde-md.md)] пользовательских баз данных может быть установлен с файлового сервера Server Message Block (SMB), использовать как хранилище. Это относится как к изолированному варианту установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и к установке кластеров отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Файловый поток в настоящее время не поддерживается в общей папке SMB.  
  
## <a name="installation-considerations"></a>Рекомендации по установке  
  
### <a name="smb-file-share-formats"></a>Форматы общей папки SMB:  
 При указании общей папки SMB путь может быть указан в одном из следующих форматов UNC для изолированных баз данных и баз данных FCI:  
  
-   \\\имя_сервера\имя_папки\  
  
-   \\\имя_сервера\имя_папки  
  
 Дополнительные сведения о формате UNC, см. в разделе [UNC](http://go.microsoft.com/fwlink/?LinkId=245534) (http://go.microsoft.com/fwlink/?LinkId=245534).  
  
 Путь UNC замыкания на себя (путь UNC, где именем сервера является localhost, 127.0.0.1 или имя локального компьютера) не поддерживается. В качестве особого случая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием кластера файлового сервера, размещенного на том же узле [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , также не поддерживается. Чтобы предотвратить возникновение этой ситуации, рекомендуется создавать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и кластер файлового сервера на отдельных кластерах Windows.  
  
 Указанные ниже форматы путей UNC не поддерживаются.  
  
-   Петлевой путь, например \\\localhost\\..\ или \\\127.0.0.1\\...\  
  
-   Административные общие папки, например \\\servername\x$  
  
-   Другие форматы путей UNC, такие как \\\\\?\x:\  
  
-   Подключенные сетевые диски.  
  
### <a name="supported-data-definition-language-ddl-statements"></a>Поддерживаемые инструкции языка описания данных DDL.  
 Следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL и хранимые процедуры компонента ядра СУБД поддерживают общие папки SMB.  
  
1.  [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
2.  [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
3.  [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
4.  [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)  
  
5.  [sp_attach_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql)  
  
6.  [sp_attach_single_file_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql)  
  
### <a name="installation-options"></a>Варианты установки  
  
-   На странице "Настройка компонента ядра СУБД" пользовательского интерфейса программы настройки перейдите на вкладку "Каталоги данных" и задайте для параметра "Корневой каталог данных" значение "\\\fileserver1\share1\".  
  
-   При установке из командной строки задайте для параметра "/INSTALLSQLDATADIR" значение "\\\fileserver1\share1\".  
  
     Ниже представлен образец синтаксиса для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на отдельном сервере с использованием общей папки SMB.  
  
    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="<StrongPassword>" /INSTALLSQLDATADIR="\\FileServer\Share1\" /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
     Установка экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с одним узлом с компонентами [!INCLUDE[ssDE](../../includes/ssde-md.md)] и службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], экземпляр по умолчанию.  
  
    ```  
    setup.exe /q /ACTION=InstallFailoverCluster /InstanceName=MSSQLSERVER /INDICATEPROGRESS /ASSYSADMINACCOUNTS="<DomainName\UserName>" /ASDATADIR=<Drive>:\OLAP\Data /ASLOGDIR=<Drive>:\OLAP\Log /ASBACKUPDIR=<Drive>:\OLAP\Backup /ASCONFIGDIR=<Drive>:\OLAP\Config /ASTEMPDIR=<Drive>:\OLAP\Temp /FAILOVERCLUSTERDISKS="<Cluster Disk Resource Name - for example, 'Disk S:'" /FAILOVERCLUSTERNETWORKNAME="<Insert Network Name>" /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;Cluster Network;xxx.xxx.xxx.x" /FAILOVERCLUSTERGROUP="MSSQLSERVER" /Features=AS,SQL /ASSVCACCOUNT="<DomainName\UserName>" /ASSVCPASSWORD="xxxxxxxxxxx" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="xxxxxxxxxxx" /INSTALLSQLDATADIR="\\FileServer\Share1\" /SQLCOLLATION="SQL_Latin1_General_CP1_CS_AS" /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="xxxxxxxxxxx" /SQLSYSADMINACCOUNTS="<DomainName\UserName> /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
     Дополнительные сведения об использовании различных параметров командной строки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], см. в разделе [Установка SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="operating-system-considerations-smb-protocol-vs-includessnoversionincludesssnoversion-mdmd"></a>Рекомендации по операционным системам (сравнение протокола SMB и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])  
 В различных операционных системах Windows используются разные версии протокола SMB. Версия протокола SMB прозрачна для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно выяснить информацию о преимуществах разных версий SMB в отношении [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Операционная система|Версия протокола SMB2|Преимущества для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|----------------------|---------------------------|-------------------------------------------|  
|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] с пакетом обновления 2 (SP2)|2.0|Повышенная производительность по сравнению с предыдущими версиями SMB.<br /><br /> Устойчивость, которая помогает восстанавливать данные при временных проблемах в работе сети.|  
|[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1), включая Server Core|2.1|Поддержка больших MTU, что позволяет передавать большой объем данных, например при резервном копировании и восстановлении SQL. Эту возможность должен включить пользователь. Дополнительные сведения о включении этой функции см. в разделе [Новые возможности SMB](http://go.microsoft.com/fwlink/?LinkID=237319) (http://go.microsoft.com/fwlink/?LinkID=237319).<br /><br /> Значительные улучшения производительности, в частности для рабочих нагрузок SQL OLTP. Эти улучшения производительности требуют применения исправления. Дополнительные сведения об этом исправлении см. в [этом разделе](http://go.microsoft.com/fwlink/?LinkId=237320) (http://go.microsoft.com/fwlink/?LinkId=237320).|  
|[!INCLUDE[win8srv](../../includes/win8srv-md.md)], включая Server Core|3.0|Поддержка прозрачных обработок отказов общих папок с нулевым временем простоев и без необходимости вмешательства администраторов для изменения SQL DBA или администраторов файловых серверов для изменения конфигурации кластеров файловых серверов.<br /><br /> Поддержка ввода-вывода с одновременным использованием нескольких сетевых интерфейсов, а также устойчивость к отказу сетевых интерфейсов.<br /><br /> Поддержка сетевых интерфейсов с возможностями RDMA.<br /><br /> Дополнительные сведения об этих возможностях и протоколе SMB см. в разделе [Общие сведения о протоколе SMB](http://go.microsoft.com/fwlink/?LinkId=253174) (http://go.microsoft.com/fwlink/?LinkId=253174).<br /><br /> Поддержка для сервера SoFS с постоянной доступностью.|  
|[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2, включая Server Core|3.2|Поддержка прозрачных обработок отказов общих папок с нулевым временем простоев и без необходимости вмешательства администраторов для изменения SQL DBA или администраторов файловых серверов для изменения конфигурации кластеров файловых серверов.<br /><br /> Поддержка ввода-вывода с одновременным использованием нескольких сетевых интерфейсов, а также устойчивость к отказу сетевых интерфейсов с помощью SMB Multichannel.<br /><br /> Поддержка сетевых интерфейсов с возможностями с помощью SMB Direct.<br /><br /> Дополнительные сведения об этих возможностях и протоколе SMB см. в разделе [Общие сведения о протоколе SMB](http://go.microsoft.com/fwlink/?LinkId=253174) (http://go.microsoft.com/fwlink/?LinkId=253174).<br /><br /> Поддержка для сервера SoFS с постоянной доступностью.<br /><br /> Оптимизировано для небольших произвольных операций ввода-вывода чтения и записи, обычных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLTP.<br /><br /> Максимальный размер пакета (MTU) включен по умолчанию, что значительно повышает производительность в больших последовательных передачах, таких как хранилище данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или резервное копирование и восстановление базы данных.|  
  
## <a name="security-considerations"></a>Вопросы безопасности  
  
-   Учетная запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и учетная запись агента службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны иметь разрешения «Полный доступ» и разрешения NTFS для общих папок SMB. При использовании файлового сервера SMB в качестве учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать учетную запись домена или системы. Дополнительные сведения о разрешениях для общей папки и NTFS см. в разделе [Разрешения для общей папки и NTFS на файловом сервере](http://go.microsoft.com/fwlink/?LinkId=245535) (http://go.microsoft.com/fwlink/?LinkId=245535).  
  
    > [!NOTE]  
    >  Полный доступ для общих папок и разрешения NTFS для общих папок SMB должны действовать только для учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользователей Windows, которым назначена роль администратора сервера.  
  
     В качестве учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рекомендуется использовать учетную запись домена. Если в качестве учетной записи службы используется учетная запись системы, предоставьте разрешения для учетной записи компьютера в формате: * < имя_домена >***\\***< имя_компьютера > ***$**.  
  
    > [!NOTE]  
    >  -   Если в качестве хранилища задана общая папка SMB, во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве учетной записи службы необходимо задать учетную запись домена. При использовании общей папки SMB учетную запись системы можно задать в качестве учетной записи службы только после установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
    > -   Виртуальные учетные записи не могут проходить проверку подлинности в удаленном расположении. Все виртуальные учетные записи используют разрешение локальной учетной записи. Укажите учетную запись компьютера в формате *<имя_домена>***\\***<имя_компьютера>***$**.  
  
-   Учетная запись, которая использовалась для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], при установке кластера должна иметь разрешение «Полный доступ» к общей папке SMB, используемой в качестве каталога данных, или к любым другим папкам данных (каталог пользовательской базы данных, каталог журналов пользовательской базы данных, папка TempDB, каталог журналов TempDB, папка резервного копирования).  
  
-   Учетная запись, используемая для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна обладать правами SeSecurityPrivilege на файловом сервере SMB. Для предоставления этого права используйте консоль локальной политики безопасности на файловом сервере, чтобы добавить учетную запись установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в политику управления журналом аудита и безопасности. Этот параметр находится в разделе «Назначение прав пользователя» в узле «Локальные политики» консоли «Локальная политика безопасности».  
  
## <a name="known-issues"></a>Известные проблемы  
  
-   После отсоединения базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , которая находится в хранилище, подключенном к сети, при попытке повторного присоединения базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возможны проблемы с разрешением доступа к базе данных. Эта проблема описывается в [этой статье базы знаний](http://go.microsoft.com/fwlink/?LinkId=237321) (http://go.microsoft.com/fwlink/?LinkId=237321). Информацию о решении этой проблемы см. в разделе **Дополнительные сведения** статьи из базы знаний.  
  
-   Некоторые решения сторонних разработчиков, например устройство NetApp, не поддерживают все вызовы API SQL Server. С этими может появиться:   
    2015-06-04 отображаться spid9s ошибка: 17053, серьезность: 16, состояние: 1.  
    2015-06-04 отображаться spid9s DoDevIoCtlOut() GetOverlappedResult(): произошла ошибка операционной системы 1 (Неправильная функция.).  
  
     Для файловой системы NTFS эта ошибка неопасна,  но в случае с ReFS она может привести к существенному снижению производительности.  
  
-   Если общая папка SMB используется в качестве хранилища для кластеризованного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то по умолчанию журнал диагностики отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть записан в общий файловый ресурс, так как у библиотеки ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нет разрешения на чтение и запись в общий файловый ресурс. Чтобы устранить эту проблему, попробуйте один из следующих методов.  
  
    1.  Предоставьте разрешения на чтение и запись в общей папке всем объектам-компьютерам в кластере.  
  
    2.  Задайте в качестве расположения журналов диагностики локальный путь к файлу. См. следующий пример.  
  
        ```sql  
        ALTER SERVER CONFIGURATION  
        SET DIAGNOSTICS LOG PATH = 'C:\logs';  
        ```  
  
## <a name="see-also"></a>См. также  
 [Планирование установки SQL Server](../../../2014/sql-server/install/planning-a-sql-server-installation.md)   
 [Инструкции по установке](../../../2014/sql-server/install/installation-how-to-topics.md)   
 [Настройка учетных записей службы Windows и разрешений](../configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  

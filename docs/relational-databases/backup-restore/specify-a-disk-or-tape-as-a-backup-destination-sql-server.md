---
title: "Указание в качестве назначения резервного копирования диска или ленты (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "устройства резервного копирования [SQL Server], ленты"
  - "резервное копирование баз данных [SQL Server], ленты"
  - "резервные копии баз данных [SQL Server], ленты"
  - "устройства резервного копирования [SQL Server], диски"
  - "дисковые устройства резервного копирования [SQL Server]"
  - "резервные копии баз данных [SQL Server], диски"
  - "резервное копирование баз данных [SQL Server], диски"
  - "резервные копии [SQL Server], создание"
  - "устройства для резервного копирования на магнитную ленту, резервное копирование"
ms.assetid: e391f452-ed8c-4b40-b846-ac3881271b94
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# Указание в качестве назначения резервного копирования диска или ленты (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается, как указать диск или ленту для резервного копирования в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Поддержка резервного копирования на ленточные устройства будет исключена в будущей версии SQL Server. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Указание в качестве назначения резервного копирования диска или ленты с помощью.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Разрешения BACKUP DATABASE и BACKUP LOG назначены по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_owner** и **db_backupoperator**.  
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна иметь разрешения на запись. Однако процедура [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Указание в качестве назначения резервного копирования диска или ленты.  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, выберите пункт **Задачи**, а затем команду **Создать резервную копию**. Откроется диалоговое окно **Резервное копирование базы данных** .  
  
4.  В разделе **Назначение** страницы **Общее** выберите **Диск** или **Лента**. Чтобы выбрать пути к 64 (или менее) дискам или накопителям на магнитной ленте, содержащим один набор носителей, нажмите кнопку **Добавить**.  
  
     Чтобы удалить носитель резервной копии, выберите его и нажмите кнопку **Удалить**. Чтобы просмотреть содержимое носителя резервной копии, выберите его и щелкните **Содержимое**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Указание в качестве назначения резервного копирования диска или ленты.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [BACKUP](../../t-sql/statements/backup-transact-sql.md) укажите этот файл или устройство и его физическое имя. В этом примере выполняется резервное копирование базы данных `AdventureWorks2012` в файл на диске `Z:\SQLServerBackups\AdventureWorks2012.Bak`.  
  
```  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
GO  
```  
  
## См. также:  
 [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)   
 [Создание резервных копий файлов и файловых групп (SQL Server)](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)   
 [Определение логического устройства резервного копирования для дискового файла (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)   
 [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
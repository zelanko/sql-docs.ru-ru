---
title: "Просмотр содержимого ленты или файла резервной копии (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "устройства резервного копирования [SQL Server], ленты"
  - "отображение содержимого резервных копий"
  - "просмотр содержимого резервных копий"
  - "устройства для резервного копирования на магнитную ленту, просмотр содержимого"
  - "резервные копии баз данных [SQL Server], просмотр содержимого"
  - "резервное копирование баз данных [SQL Server], просмотр содержимого"
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Просмотр содержимого ленты или файла резервной копии (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается просмотр содержимого ленты или файла резервной копии в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Поддержка резервного копирования на ленточные устройства будет исключена в будущей версии SQL Server. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Просмотр содержимого ленты или файла резервной копии с помощью следующих средств**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
 Сведения о безопасности см. в статье [RESTORE HEADERONLY (Transact-SQL)](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md).  
  
####  <a name="Permissions"></a> Разрешения  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях для получения сведений о резервном наборе данных или устройстве резервного копирования необходимо разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Просмотр содержимого ленты или файла резервной копии  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, резервную копию которой хотите создать, укажите пункт **Задачи** и выберите команду **Создать резервную копию**. Откроется диалоговое окно **Резервное копирование базы данных** .  
  
4.  В области **Назначение** страницы **Общие** выберите **Диск** или **Лента**. В списке **Создать резервную копию на** выберите нужный файл на диске или ленту.  
  
     Если дисковый файл или лента отсутствуют в списке, нажмите кнопку **Добавить**. Выберите имя файла или ленточный накопитель. Чтобы добавить его в список **Создать резервную копию на**, нажмите кнопку **ОК**.  
  
5.  В списке **Создать резервную копию на** выберите путь к диску или ленточному накопителю, который необходимо просмотреть, и нажмите кнопку **Содержимое**. Откроется диалоговое окно **Содержимое устройства** .  
  
6.  На правой панели выводятся сведения о наборе носителей и резервных наборах данных на выбранной ленте или в файле.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Просмотр содержимого ленты или файла резервной копии  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Используйте инструкцию [RESTORE HEADERONLY](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md) . Этот пример возвращает сведения о файле `AdventureWorks2012-FullBackup.bak`.  
  
```tsql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## См. также:  
 [backupfilegroup (Transact-SQL)](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupfile (Transact-SQL)](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [backupmediaset (Transact-SQL)](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupmediafamily (Transact-SQL)](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Определение логического устройства резервного копирования для дискового файла (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
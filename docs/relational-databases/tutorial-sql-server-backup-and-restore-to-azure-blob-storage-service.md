---
title: "Tutorial: SQL Server Backup and Restore to Windows Azure Blob Storage Service | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016 Preview"
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Tutorial: SQL Server Backup and Restore to Windows Azure Blob Storage Service
Добро пожаловать в учебник «Приступая к резервному копированию и восстановлению данных SQL Server при помощи службы хранилищ больших двоичных объектов Windows Azure». С помощью этого учебника вы научитесь создавать и восстанавливать резервные копии с помощью службы хранилища больших двоичных объектов Windows Azure.  
  
## Обзор учебника  
В этом учебнике показано, как создать учетную запись хранения Windows, контейнер больших двоичных объектов, учетные данные для доступа к учетной записи хранения, как записать резервную копию в службу хранилищ больших двоичных объектов и выполнить простое восстановление. Учебник разделен на четыре занятия.  
  
[Урок 1. Создание объектов хранения Windows Azure](../Topic/Lesson%201:%20Create%20Windows%20Azure%20Storage%20Objects.md)  
На этом занятии вы создадите учетную запись хранения Windows Azure и контейнер больших двоичных объектов.  
  
[Lesson 2: Create a SQL Server Credential](../Topic/Lesson%202:%20Create%20a%20SQL%20Server%20Credential.md)  
На этом занятии вы также создадите учетные данные для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Windows Azure.  
  
[Занятие 3: Запись полной резервной копии в службу хранилища Windows Azure BLOB-объектов](../Topic/Lesson%203:%20Write%20a%20Full%20Database%20Backup%20to%20the%20Windows%20Azure%20Blob%20Storage%20Service.md)  
Кроме того, на этом занятии вам предстоит выполнить инструкцию Т-SQL для записи резервной копии базы данных AdventureWorks2012 в службу хранилищ больших двоичных объектов Windows Azure.  
  
[Занятие 4: Выполните восстановление из полной резервной копии](../Topic/Lesson%204:%20Perform%20a%20Restore%20From%20a%20Full%20Database%20Backup.md)  
На этом занятии также предстоит выполнить инструкцию T-SQL для восстановления из резервной копии базы данных, созданной на предыдущем занятии.  
  
### Требования  
Для работы с этим учебником необходимо ознакомиться с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] резервного копирования и восстановления концепции и синтаксиса T-SQL. Для работы с этим учебником должны быть выполнены следующие требования.  
  
-   Установленный экземпляр [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]и база данных AdventureWorks2012.  
  
    Экземпляр SQL Server может быть установлен на локальном компьютере или в виртуальной машине Windows Azure.  
  
    Вместо базы данных AdventureWorks2012 можно использовать пользовательскую базу данных, соответственно изменив синтаксис инструкций T-SQL.  
  
-   Учетная запись пользователя, применяемая для выдачи команды BACKUP или RESTORE, должна находиться в роли базы данных **db_backup operator** с разрешениями **Alter any credential**.  
  
### Дополнительные материалы  
Чтобы разобраться в концепциях и рекомендуемых методах использования службы хранилищ больших двоичных объектов Windows Azure для резервного копирования [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , рекомендуется изучить перечисленные ниже материалы.  
  
1.  [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
## См. также:  
[Создание резервной копии базы данных и журнала](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#databaselog)  
[Создание полной резервной копии первичной файловой группы](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#filegroups)  
[Восстановление базы данных и перемещение файлов](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#restoredbwithmove)  
  

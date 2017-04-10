---
title: "Удаление устройства резервного копирования (SQL Server) | Microsoft Docs"
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
  - "резервные копии баз данных [SQL Server], удаление устройств"
  - "устройства резервного копирования [SQL Server], удаление"
  - "удаление устройств резервного копирования"
  - "удаление устройств резервного копирования"
  - "резервное копирование баз данных [SQL Server], устройства резервного копирования"
ms.assetid: 7be62480-ed6a-4262-a071-1feba73b1c02
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# Удаление устройства резервного копирования (SQL Server)
  В этом разделе описывается, как удалить резервное устройство в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Удаление устройства резервного копирования с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требует членства в предопределенной роли сервера **diskadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Удаление устройства резервного копирования  
  
1.  После подключения к соответствующему экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув имя сервера.  
  
2.  Разверните узел **Объекты сервера**, затем разверните узел **Устройства резервного копирования**.  
  
3.  Щелкните правой кнопкой мыши устройство, которое нужно удалить, и выберите команду **Удалить**.  
  
4.  В диалоговом окне **Удаление объекта** убедитесь, что в столбце **Имя объекта** отображается нужное имя.  
  
5.  Нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Удаление устройства резервного копирования  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в запрос. В этом примере показано, как использовать инструкцию [sp_dropdevice](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md) для удаления устройства резервного копирования. Выполните первый пример для создания устройства резервного копирования `mybackupdisk` и физического имени `c:\backup\backup1.bak`. Выполните инструкцию **sp_dropdevice** для удаления устройства резервного копирования `mybackupdisk`. Параметр `delfile` удаляет физическое имя.  
  
```tsql  
--Define a backup device and physical name.   
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mybackupdisk', 'c:\backup\backup1.bak' ;  
GO  
--Delete the backup device and the physical name.  
USE AdventureWorks2012 ;  
GO  
EXEC sp_dropdevice ' mybackupdisk ', 'delfile' ;  
GO  
  
```  
  
## См. также:  
 [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)   
 [sys.backup_devices (Transact-SQL)](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)  
  
  
---
title: "Отображение данных и сведений о пространстве журнала для базы данных | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "журналы [SQL Server], пространство"
  - "сведения о состоянии [SQL Server], пространство"
  - "отображение сведений о пространстве"
  - "место на диске [SQL Server], отображение"
  - "базы данных [SQL Server], занятое пространство"
  - "просмотр сведений о состоянии"
  - "выделение пространства [SQL Server], отображение"
  - "пространство данных [SQL Server]"
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Отображение данных и сведений о пространстве журнала для базы данных
  В этом разделе описано, как отобразить данные и сведения о пространстве журнала для базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  

  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Разрешение на выполнение процедуры **sp_spaceused** предоставлено роли **public**. Параметр **@updateusage** могут указывать только члены предопределенной роли базы данных **db_owner**.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Отображение данных и сведений о пространстве для базы данных  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**.  
  
3.  Щелкните правой кнопкой мыши базу данных, укажите **Отчеты**, **Стандартные отчеты**, а затем щелкните **Использование диска**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Отображение данных и сведений о пространстве журнала для базы данных при помощи процедуры sp_spaceused  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется системная хранимая процедура [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md), которая передает сведения о заполнении места на диске для таблицы `Vendor` и ее индексов.  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### Отображение данных и сведений о пространстве журнала для базы данных путем запроса к представлению каталога sys.database_files  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется запрос к представлению каталога [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md), который возвращает определенные сведения о файлах данных и журнала из базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [Добавление файлов данных или журналов в базу данных](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [Удаление файлов данных или журнала из базы данных](../../relational-databases/databases/delete-data-or-log-files-from-a-database.md)  
  
  
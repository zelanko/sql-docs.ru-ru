---
title: Отображение данных и сведений о пространстве журнала для базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], space
- status information [SQL Server], space
- displaying space information
- disk space [SQL Server], displaying
- databases [SQL Server], space used
- viewing space information
- space allocation [SQL Server], displaying
- data space [SQL Server]
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4850be4c112f9c0b987d543873cb55af08372455
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917359"
---
# <a name="display-data-and-log-space-information-for-a-database"></a>Отображение данных и сведений о пространстве журнала для базы данных
  В этом разделе описано, как отобразить данные и сведения о пространстве журнала для базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Отображение данных и сведений о пространстве для базы данных, с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешение на выполнение процедуры **sp_spaceused** предоставлено роли **public** . Параметр **@updateusage** могут указывать только члены предопределенной роли базы данных **@updateusage** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-display-data-and-log-space-information-for-a-database"></a>Отображение данных и сведений о пространстве для базы данных  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**.  
  
3.  Щелкните правой кнопкой мыши базу данных, укажите **Отчеты**, **Стандартные отчеты**, а затем щелкните **Использование диска**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-using-spspaceused"></a>Отображение данных и сведений о пространстве журнала для базы данных при помощи процедуры sp_spaceused  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется системная хранимая процедура [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) , которая передает сведения о заполнении места на диске для таблицы `Vendor` и ее индексов.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabasefiles"></a>Отображение данных и сведений о пространстве журнала для базы данных путем запроса к представлению каталога sys.database_files  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется запрос к представлению каталога [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) , который возвращает определенные сведения о файлах данных и журнала из базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)   
 [sp_spaceused (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql)   
 [Добавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md)   
 [Удаление файлов данных или журнала из базы данных](delete-data-or-log-files-from-a-database.md)  
  
  

---
title: Отображение данных и сведений о пространстве журнала для базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2cf9ac822df456439a9df7ef60b15f33d6c93b3e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102481"
---
# <a name="display-data-and-log-space-information-for-a-database"></a>Отображение данных и сведений о пространстве журнала для базы данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В этом разделе описано, как отобразить данные и сведения о пространстве журнала для базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  

  
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
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется системная хранимая процедура [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) , которая передает сведения о заполнении места на диске для таблицы `Vendor` и ее индексов.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabasefiles"></a>Отображение данных и сведений о пространстве журнала для базы данных путем запроса к представлению каталога sys.database_files  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется запрос к представлению каталога [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) , который возвращает определенные сведения о файлах данных и журнала из базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [Добавление файлов данных или журналов в базу данных](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [Удаление файлов данных или журнала из базы данных](../../relational-databases/databases/delete-data-or-log-files-from-a-database.md)  
  
  

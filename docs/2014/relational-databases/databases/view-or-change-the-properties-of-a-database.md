---
title: Просмотр или изменение свойств базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10ad92286011f6f81fbaff5ab4908007e16bdd45
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528469"
---
# <a name="view-or-change-the-properties-of-a-database"></a>Просмотр или изменение свойств базы данных
  В этом разделе описывается просмотр и изменение свойств базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. После задания нового значения свойства базы данных изменение вступает в силу немедленно.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Просмотр или изменение свойств базы данных различными средствами**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Если параметр AUTO_CLOSE имеет значение ON, некоторые столбцы в представлении каталога [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) и функция DATABASEPROPERTYEX будут возвращать значение NULL, так как база данных будет недоступна для извлечения данных. Для решения этой проблемы выполните инструкцию USE, чтобы открыть базу данных.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a>Просмотр или изменение свойств базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Базы данных**, правой кнопкой мыши щелкните базу данных для просмотра, затем выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства базы данных** выберите страницу, чтобы просмотреть соответствующие сведения. Например, выберите страницу **Файлы** , чтобы просмотреть сведения о файлах данных и журнала.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a>Просмотр свойства базы данных с помощью функции DATABASEPROPERTYEX  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется системная функция [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) , предназначенная для возвращения состояния параметра базы данных AUTO_SHRINK в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Возвращенное значение 1 означает, что этот параметр установлен в значение ON, а возвращенное значение 0, означает, что параметр имеет значение OFF.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a>Просмотр свойств базы данных при помощи запроса к представлению каталога sys.databases  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется опрос к представлению каталога [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) для просмотра нескольких свойств базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . В этом примере возвращается идентификационный номер базы данных (`database_id`), вне зависимости от того, предназначена ли она только для чтения или для чтения и записи (`is_read_only`), параметры сортировки базы данных (`collation_name`) и уровень совместимости базы данных (`compatibility_level`).  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a>Изменение свойств базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса. В этом примере определяется состояние изоляции моментального снимка в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , выполняется изменение состояния этого свойства и выполняется проверка изменения.  
  
     Чтобы определить состояние изоляции моментального снимка, выберите первую инструкцию `SELECT` и нажмите кнопку **Выполнить**.  
  
     Чтобы изменить состояние изоляции моментального снимка, выберите инструкцию `ALTER DATABASE` и нажмите кнопку **Выполнить**.  
  
     Чтобы проверить изменение, выберите вторую инструкцию `SELECT` и нажмите кнопку **Выполнить**.  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a>См. также  
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [ALTER DATABASE SET HADR (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)   
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)   
 [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  

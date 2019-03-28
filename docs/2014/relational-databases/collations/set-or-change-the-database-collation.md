---
title: Установка и изменение параметров сортировки базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], database
- database collations [SQL Server]
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 38c29f8d70b3cc72baf81e2ae23082fe270ba573
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537396"
---
# <a name="set-or-change-the-database-collation"></a>Установка и изменение параметров сортировки базы данных
  В этом разделе описано, как задать и изменить параметры сортировки базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если параметры сортировки не указаны, используются параметры сортировки сервера.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Задание и изменение параметров сортировки базы данных с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Параметры сортировки Windows только для Юникода могут использоваться только с предложением COLLATE для применения параметров сортировки к данным типов `nchar`, `nvarchar` и `ntext` на уровне столбца и на уровне выражения. Их нельзя использовать с предложением COLLATE для изменения параметров сортировки базы данных или экземпляра сервера.  
  
-   Если указанные или используемые объектом по ссылке параметры сортировки используют кодовую страницу, не поддерживаемую Windows, то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выдаст ошибку.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Имена поддерживаемых параметров сортировки вы можете найти в статьях [Имя параметров сортировки Windows (Transact-SQL)](/sql/t-sql/statements/windows-collation-name-transact-sql) и [Имя параметров сортировки SQL Server (Transact-SQL)](/sql/t-sql/statements/sql-server-collation-name-transact-sql)или воспользоваться системной функцией [sys.fn_helpcollations (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) .  
  
-   Если изменяются параметры сортировки базы данных, то изменяется следующее:  
  
    -   Все столбцы типа `char`, `varchar`, `text`, `nchar`, `nvarchar` или `ntext` в системных таблицах заменяются новым параметром сортировки.  
  
    -   Все существующие параметры типа `char`, `varchar`, `text`, `nchar`, `nvarchar` или `ntext` и возвращаемые скалярные значения для хранимых процедур и определяемых пользователем функций заменяются новым параметром сортировки.  
  
    -   Системные типы данных `char`, `varchar`, `text`, `nchar`, `nvarchar` и `ntext` и все определяемые пользователем типы данных, основанные на этих системных типах данных, заменяются новым параметром сортировки по умолчанию.  
  
-   Можно изменить параметры сортировки любых новых объектов, созданных в пользовательской базе данных, с помощью предложения COLLATE инструкции [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) . Эта инструкция не изменяет параметры сортировки столбцов в любых существующих пользовательских таблицах. Он может быть изменен с помощью предложения COLLATE инструкции [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 CREATE DATABASE  
 Требуется разрешение CREATE DATABASE в базе данных **master** или разрешение CREATE ANY DATABASE или ALTER ANY DATABASE.  
  
 ALTER DATABASE  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-set-or-change-the-database-collation"></a>Задание и изменение параметров сортировки базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], разверните его, а затем разверните узел **Базы данных**.  
  
2.  При создании новой базы данных щелкните правой кнопкой мыши **Базы данных** и выберите пункт **Создать базу данных**. Если использовать параметры сортировки по умолчанию не нужно, то перейдите на страницу **Параметры** и выберите нужный вариант в раскрывающемся списке **Параметры сортировки** .  
  
     Если база данных уже существует, щелкните правой кнопкой мыши нужную базу данных и выберите пункт **Свойства**. Перейдите на страницу **Параметры** , а затем выберите нужный вариант в раскрывающемся списке **Параметры сортировки** .  
  
3.  По завершении нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-set-the-database-collation"></a>Задание параметров сортировки базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано задание параметров сортировки с помощью предложения [COLLATE](/sql/t-sql/statements/collations) . В примере создается база данных `MyOptionsTest` , в которой используются параметры сортировки `Latin1_General_100_CS_AS_SC` . Чтобы проверить параметр, после создания базы данных выполните инструкцию `SELECT` .  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE Latin1_General_100_CS_AS_SC;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
#### <a name="to-change-the-database-collation"></a>Изменение параметров сортировки базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано изменение имени параметров сортировки с помощью предложения [COLLATE](/sql/t-sql/statements/collations) в инструкции [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) . Выполните инструкцию `SELECT` , чтобы проверить изменение.  
  
```sql  
USE master;  
GO  
ALTER DATABASE MyOptionsTest  
COLLATE French_CI_AS ;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [Поддержка параметров сортировки и Юникода](collation-and-unicode-support.md)   
 [sys.fn_helpcollations (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql)   
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [Имя параметров сортировки SQL Server (Transact-SQL)](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [Имя параметров сортировки Windows (Transact-SQL)](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [COLLATE (Transact-SQL)](/sql/t-sql/statements/collations)   
 [Очередность параметров сортировки (Transact-SQL)](/sql/t-sql/statements/collation-precedence-transact-sql)   
 [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql)   
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)   
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
  

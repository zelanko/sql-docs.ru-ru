---
title: "Просмотр сведений о параметрах сортировки | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: eebc43acb7df6cf2d63dbc6d8e0d1c4f25fa9476
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="view-collation-information"></a>Просмотр сведений о параметрах сортировки
    
##  <a name="Top"></a> Просмотреть параметры сортировки сервера, базы данных или столбца в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно, используя команды меню обозревателя объектов или при помощи инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
##  <a name="Procedures"></a> Как просмотреть параметры сортировки  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр параметров сортировки для сервера (экземпляра SQL Server) в обозревателе объектов.**  
  
1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Щелкните экземпляр правой кнопкой мыши и выберите пункт **Свойства**.  
  
 **Просмотр параметров сортировки для базы данных в обозревателе объектов**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, щелкните базу данных правой кнопкой мыши и выберите пункт **Свойства**.  
  
 **Просмотр параметров сортировки для столбца в обозревателе объектов**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных и узел **Таблицы**.  
  
3.  Разверните таблицу, содержащую столбец и затем разверните **Столбцы**.  
  
4.  Щелкните правой кнопкой мыши столбец и выберите команду **Свойства**. Если параметры сортировки не указаны, то данный столбец не относится к символьному типу данных.  
  
###  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр параметров сортировки для сервера**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и выберите на панели инструментов команду **Создать запрос**.  
  
2.  В окне запроса введите следующую инструкцию, которая использует системную функцию SERVERPROPERTY.  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  Кроме того, можно использовать системную хранимую процедуру sp_helpsort.  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 **Просмотр всех параметров сортировки, поддерживаемых [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и выберите на панели инструментов команду **Создать запрос**.  
  
2.  В окне запроса введите следующую инструкцию, которая использует системную функцию SERVERPROPERTY.  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 **Просмотр параметров сортировки для базы данных**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и выберите на панели инструментов команду **Создать запрос**.  
  
2.  В окне запроса введите следующую инструкцию, которая использует системное представление каталога sys.databases.  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  Кроме того, можно использовать системную функцию DATABASEPROPERTYEX.  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 **Просмотр параметров сортировки для столбца**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и выберите на панели инструментов команду **Создать запрос**.  
  
2.  В окне запроса введите следующую инструкцию, которая использует системное представление каталога sys.columns.  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a>См. также:  
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sys.fn_helpcollations (Transact-SQL)](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Очередность параметров сортировки (Transact-SQL)](../../t-sql/statements/collation-precedence-transact-sql.md)   
 [sp_helpsort (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsort-transact-sql.md)  
  
  

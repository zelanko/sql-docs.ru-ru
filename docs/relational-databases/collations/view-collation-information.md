---
title: Просмотр сведений о параметрах сортировки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5d03fde715ba1f7edcfa89d6f5b6955e0543c121
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765843"
---
# <a name="view-collation-information"></a>Просмотр сведений о параметрах сортировки
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
<a name="Top"></a> Просмотреть параметры сортировки сервера, базы данных или столбца в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно, используя команды меню обозревателя объектов или при помощи инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
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
  
    ```sql  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  Кроме того, можно использовать системную хранимую процедуру sp_helpsort.  
  
    ```sql  
    EXECUTE sp_helpsort;  
    ```  
  
 **Просмотр всех параметров сортировки, поддерживаемых [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и выберите на панели инструментов команду **Создать запрос**.  
  
2.  В окне запроса введите следующую инструкцию, которая использует системную функцию SERVERPROPERTY.  
  
    ```sql  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 **Просмотр параметров сортировки для базы данных**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и выберите на панели инструментов команду **Создать запрос**.  
  
2.  В окне запроса введите следующую инструкцию, которая использует системное представление каталога sys.databases.  
  
    ```sql  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  Кроме того, можно использовать системную функцию DATABASEPROPERTYEX.  
  
    ```sql  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 **Просмотр параметров сортировки для столбца**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и выберите на панели инструментов команду **Создать запрос**.  
  
2.  В окне запроса введите следующую инструкцию, которая использует системное представление каталога sys.columns.  
  
    ```sql  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a>См. также:  
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sys.fn_helpcollations (Transact-SQL)](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Очередность параметров сортировки (Transact-SQL)](../../t-sql/statements/collation-precedence-transact-sql.md)   
 [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)      
 [sp_helpsort (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsort-transact-sql.md)  
  
  

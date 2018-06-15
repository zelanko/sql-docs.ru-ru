---
title: Просмотр или изменение свойств базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/05/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
caps.latest.revision: 42
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 72fc29742d0bc23e9a6d341071d529f1ffe74ade
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32930899"
---
# <a name="view-or-change-the-properties-of-a-database"></a>Просмотр или изменение свойств базы данных
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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
  
-   Если параметр AUTO_CLOSE имеет значение ON, некоторые столбцы в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) и функция DATABASEPROPERTYEX будут возвращать значение NULL, так как база данных будет недоступна для извлечения данных. Чтобы устранить эту проблему, откройте базу данных.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для изменения свойств базы данных необходимо разрешение ALTER на базу данных. Для просмотра свойств базы данных требуется по крайней мере членство в роли базы данных public.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a>Просмотр или изменение свойств базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Базы данных**, правой кнопкой мыши щелкните базу данных для просмотра, затем выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства базы данных** выберите страницу, чтобы просмотреть соответствующие сведения. Например, выберите страницу **Файлы** , чтобы просмотреть сведения о файлах данных и журнала.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Transact-SQL предоставляет ряд различных методов для просмотра и изменения свойств базы данных. Чтобы просмотреть свойства базы данных, можно использовать функцию [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md) и представление каталога [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) . Чтобы изменить свойства базы данных, можно воспользоваться версией инструкции ALTER DATABASE для вашей среды: [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md) или [ALTER DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md). Для просмотра свойств уровня базы данных воспользуйтесь представлением каталога [sys.database_scoped_configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) , а для изменения свойств уровня базы данных — инструкцией [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) .  
  
#### <a name="to-view-a-property-of-a-database-by-using-the-databasepropertyex-function"></a>Просмотр свойств базы данных с использованием функции DATABASEPROPERTYEX  
  
1.  Подключитесь к [!INCLUDE[ssDE](../../includes/ssde-md.md)] , а затем к базе данных, свойства которой нужно просмотреть.  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется системная функция [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) , предназначенная для возвращения состояния параметра базы данных AUTO_SHRINK в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Возвращенное значение 1 означает, что этот параметр установлен в значение ON, а возвращенное значение 0, означает, что параметр имеет значение OFF.  
  
    ```sql  
    SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
    ```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a>Просмотр свойств базы данных при помощи запроса к представлению каталога sys.databases  
  
1.  Подключитесь к [!INCLUDE[ssDE](../../includes/ssde-md.md)] , а затем к базе данных, свойства которой нужно просмотреть.  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется опрос к представлению каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) для просмотра нескольких свойств базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . В этом примере возвращается идентификационный номер базы данных (`database_id`), вне зависимости от того, предназначена ли она только для чтения или для чтения и записи (`is_read_only`), параметры сортировки базы данных (`collation_name`) и уровень совместимости базы данных (`compatibility_level`).  
  
    ```sql  
    SELECT database_id, is_read_only, collation_name, compatibility_level  
    FROM sys.databases WHERE name = 'AdventureWorks2012';  
    ```  
  
#### <a name="to-view-the-properties-of-a-database-scoped-configuration-by-querying-sysdatabasesscopedconfiguration"></a>Просмотр свойств конфигурации уровня базы данных путем запроса sys.databases_scoped_configuration  
  
1.  Подключитесь к [!INCLUDE[ssDE](../../includes/ssde-md.md)] , а затем к базе данных, свойства которой нужно просмотреть.  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется опрос к представлению каталога [sys.database_scoped_configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) запрашивается для просмотра нескольких свойств текущей базы данных.  
  
    ```sql  
    SELECT configuration_id, name, value, value_for_secondary  
    FROM sys.database_scoped_configurations;  
    ```  
  
     Дополнительные примеры см. в разделе [sys.database_scoped_configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)  
  
#### <a name="to-change-the-properties-of-a-sql-server-2016-database-using-alter-database"></a>Изменение свойств базы данных SQL Server 2016 с помощью инструкции ALTER DATABASE  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса. В этом примере определяется состояние изоляции моментального снимка в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , выполняется изменение состояния этого свойства и выполняется проверка изменения.  
  
     Чтобы определить состояние изоляции моментального снимка, выберите первую инструкцию `SELECT` и нажмите кнопку **Выполнить**.  
  
     Чтобы изменить состояние изоляции моментального снимка, выберите инструкцию `ALTER DATABASE` и нажмите кнопку **Выполнить**.  
  
     Чтобы проверить изменение, выберите вторую инструкцию `SELECT` и нажмите кнопку **Выполнить**.  
  
     [!code-sql[DatabaseDDL#AlterDatabase9](../../relational-databases/databases/codesnippet/tsql/view-or-change-the-prope_1.sql)]  
  
#### <a name="to-change-the-database-scoped-properties-using-alter-database-scoped-configuration"></a>Изменение свойств уровня базы данных с помощью инструкции ALTER DATABASE SCOPED CONFIGURATION  
  
1.  Подключитесь к базе данных в экземпляре SQL Server.  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса. В следующем примере задается MAXDOP для базы данных-получателя в качестве значения для базы данных-источника.  
  
    ```sql  
    ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP = PRIMARY   
    ```  
  
## <a name="see-also"></a>См. также:  
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [sys.database_scoped_configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)  

  
  

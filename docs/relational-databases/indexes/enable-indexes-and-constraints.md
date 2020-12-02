---
description: Включение индексов и ограничений
title: Включение индексов и ограничений | Документация Майкрософт
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], enabling
- nonclustered indexes [SQL Server], enabling a disabled index
- index enabling [SQL Server]
- disabled indexes [SQL Server], how to enable
- constraints [SQL Server], enabling
- clustered indexes, enabling disabled indexes
ms.assetid: c55c8865-322e-4ab0-ba04-ea1f56735353
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4b0bdb3d9edca685e3b939c5f9a3ab1a0ec68846
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96130270"
---
# <a name="enable-indexes-and-constraints"></a>Включение индексов и ограничений
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  В этом разделе описывается включение отключенного индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. После отключения индекс остается в отключенном состоянии до тех пор, пока он не будет перестроен или удален.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Включение отключенного индекса с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   После перестроения индекса нужно вручную включить все ограничения, которые были отключены из-за отключения индекса. Ограничения PRIMARY KEY и UNIQUE включаются путем перестроения соответствующего индекса. Индекс должен быть перестроен (включен) до включения ограничений FOREIGN KEY, которые ссылаются на ограничение PRIMARY KEY или UNIQUE. Ограничения FOREIGN KEY включаются с помощью инструкции ALTER TABLE CHECK CONSTRAINT.  
  
-   Перестройка отключенного кластеризованного индекса не может быть выполнена, если параметр ONLINE имеет значение ON.  
  
-   Когда кластеризованный индекс отключен или включен, а некластеризованный индекс отключен, действие кластеризованного индекса на отключенный некластеризованный индекс дает следующие результаты.  
  
    |Действие кластеризованного индекса|Отключенный некластеризованный индекс ...|  
    |----------------------------|-----------------------------------|  
    |ALTER INDEX REBUILD.|Остается отключенным.|  
    |ALTER INDEX ALL REBUILD.|Будет перестроен и включен.|  
    |DROP INDEX.|Остается отключенным.|  
    |CREATE INDEX WITH DROP_EXISTING.|Остается отключенным.|  
  
     При создании нового кластеризованного индекса работает аналогично инструкции ALTER INDEX ALL REBUILD.  
  
-   Разрешенные действия на некластеризованных индексах, связанных с кластеризованным индексом, зависят от состояния (отключен или включен) обоих типов индекса. Следующая таблица обобщает разрешенные действия на некластеризованных индексах.  
  
    |Действие некластеризованного индекса|Когда и кластеризованные, и некластеризованные индексы отключены.|Когда кластеризованный индекс включен, а некластеризованный индекс либо отключен, либо включен.|  
    |-------------------------------|--------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
    |ALTER INDEX REBUILD.|Не удалось выполнить операцию.|Операция выполнена успешно.|  
    |DROP INDEX.|Операция выполнена успешно.|Операция выполнена успешно.|  
    |CREATE INDEX WITH DROP_EXISTING.|Не удалось выполнить операцию.|Операция выполнена успешно.|  

-   При перестроении отключенных сжатых некластеризованных индексов параметр data_compression по умолчанию имеет значение none. Это означает, что индексы не будут сжиматься. Связано это с тем, что при отключении некластеризованных индексов метаданные параметров сжатия теряются. Чтобы обойти эту проблему, необходимо явно настроить сжатие данных в инструкции перестроения.

###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER для таблицы или представления. При использовании инструкции DBCC DBREINDEX пользователь должен быть владельцем таблицы, членом предопределенной роли сервера **sysadmin** либо предопределенной роли базы данных **db_ddladmin** или **db_owner**.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-enable-a-disabled-index"></a>Включение отключенного индекса  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть базу данных, содержащую таблицу, в которой необходимо включить индекс.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните знак «плюс», чтобы развернуть таблицу, в которой необходимо включить индекс.  
  
4.  Чтобы развернуть папку **Индексы** , щелкните знак «плюс» (+).  
  
5.  Щелкните правой кнопкой мыши индекс, который необходимо включить, и выберите пункт **Перестроить**.  
  
6.  В диалоговом окне **Перестроение индексов** убедитесь, что нужный индекс приведен в сетке **Индексы для перестройки** и нажмите кнопку **ОК**.  
  
#### <a name="to-enable-all-indexes-on-a-table"></a>Включение всех индексов таблицы  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть базу данных, содержащую таблицу, в которой необходимо включить индексы.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните знак «плюс», чтобы развернуть таблицу, в которой необходимо включить индексы.  
  
4.  Щелкните правой кнопкой мыши папку **Индексы** и выберите **Перестроить все**.  
  
5.  В диалоговом окне **Перестройка индексов** убедитесь, что нужные индексы приведены в сетке **Индексы для перестроения** и нажмите кнопку **ОК**. Для удаления индекса из сетки **Индексы для перестроения** выделите индекс и нажмите клавишу DELETE.  
  
 В диалоговом окне **Перестроение индексов** приведены следующие сведения:  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-enable-a-disabled-index-using-alter-index"></a>Использование инструкции ALTER INDEX для включения отключенного индекса  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table.  
  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    REBUILD;   
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-create-index"></a>Использование инструкции CREATE INDEX для включения отключенного индекса  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- re-creates the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    -- using the OrganizationLevel and OrganizationNode columns  
    -- and then deletes the existing IX_Employee_OrganizationLevel_OrganizationNode index  
    CREATE INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
       (OrganizationLevel, OrganizationNode)  
    WITH (DROP_EXISTING = ON);  
    GO  
    ```  
  
#### <a name="to-enable-a-disabled-index-using-dbcc-dbreindex"></a>Использование инструкции DBCC DBREINDEX для включения отключенного индекса  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", IX_Employee_OrganizationLevel_OrganizationNode);  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-alter-index"></a>Использование инструкции ALTER INDEX для включения всех индексов в таблице  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    ALTER INDEX ALL ON HumanResources.Employee  
    REBUILD;  
    GO  
    ```  
  
#### <a name="to-enable-all-indexes-on-a-table-using-dbcc-dbreindex"></a>Использование инструкции DBCC DBREINDEX для включения всех индексов в таблице  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- enables all indexes  
    -- on the HumanResources.Employee table  
    DBCC DBREINDEX ("HumanResources.Employee", " ");  
    GO  
    ```  
  
 Дополнительные сведения см. в разделах [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md), [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md) и [DBCC DBREINDEX (Transact-SQL)](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md).  
  
  

---
title: "Включение или отключение структуры плана. | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "структуры планов [SQL Server], отключение"
  - "включение структур планов"
  - "структуры планов [SQL Server], включение"
  - "отключение структур планов"
ms.assetid: b00ab550-5308-4cb8-8330-483cd1d25654
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Включение или отключение структуры плана.
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] отключать и включать руководства планов можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Включить или отключить можно как одно руководство планов, так и все сразу.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Отключение и включение руководств планов с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Попытка удаления или изменения функции, хранимой процедуры или триггера DML, на которые имеется ссылка в структуре плана (как включенных, так и отключенных), приводит к ошибке. Всегда проверяйте зависимости перед удалением или изменением любого из объектов, перечисленных выше.  
  
-   Отключение уже отключенной структуры плана или включение включенной не имеет силы и не вызывает ошибки.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для отключения или включения структуры плана OBJECT необходимо разрешение ALTER для того объекта (например функции, хранимой процедуры), на который ссылается структура плана. Все остальные структуры планов требуют разрешения ALTER DATABASE.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Включение или отключение структуры плана  
  
1.  Щелкните значок «+», чтобы развернуть базу данных, в которой требуется включить или отключить структуру плана, затем щелкните значок «+», чтобы развернуть папку **Программирование** .  
  
2.  Щелкните значок «+», чтобы развернуть папку **Структуры планов** .  
  
3.  Правой кнопкой мыши щелкните ту структуру плана, которую требуется включить или отключить, затем выберите команду **Отключить** или **Включить**.  
  
4.  В диалоговом окне **Отключение структуры плана** или **Включение структуры плана** убедитесь, что выбранное действие выполнено успешно, и нажмите кнопку **Закрыть**.  
  
#### Отключение или включение всех структур планов в базе данных  
  
1.  Щелкните значок «+», чтобы развернуть базу данных, в которой требуется включить или отключить структуру плана, затем щелкните значок «+», чтобы развернуть папку **Программирование** .  
  
2.  Правой кнопкой мыши щелкните папку **Структуры планов**, после чего выберите команду **Включить все** или **Отключить все**.  
  
3.  В диалоговом окне **Отключение всех структур планов** или **Включение всех структур планов** убедитесь, что выбранное действие выполнено успешно, и нажмите кнопку **Закрыть**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Включение или отключение структуры плана  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    --Create a procedure on which to define the plan guide.  
    IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetSalesOrderByCountry;  
    GO  
    CREATE PROCEDURE Sales.GetSalesOrderByCountry   
        (@Country nvarchar(60))  
    AS  
    BEGIN  
        SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country;  
    END  
    GO  
    --Create the plan guide.  
    EXEC sp_create_plan_guide N'Guide3',  
        N'SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country',  
        N'OBJECT',  
        N'Sales.GetSalesOrderByCountry',  
        NULL,  
        N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
    --Disable the plan guide.  
    EXEC sp_control_plan_guide N'DISABLE', N'Guide3';  
    GO  
    --Enable the plan guide.  
    EXEC sp_control_plan_guide N'ENABLE', N'Guide3';  
    GO  
  
    ```  
  
#### Отключение или включение всех структур планов в базе данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    --Disable all plan guides in the database.  
    EXEC sp_control_plan_guide N'DISABLE ALL';  
    GO  
    --Enable all plan guides in the database.  
    EXEC sp_control_plan_guide N'ENABLE ALL';  
    GO  
  
    ```  
  
 Дополнительные сведения см. в разделе [sp_control_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md).  
  
  
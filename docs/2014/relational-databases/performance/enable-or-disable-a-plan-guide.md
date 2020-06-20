---
title: Включение или отключение структуры плана | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], disabling
- enabling plan guides
- plan guides [SQL Server], enabling
- disabling plan guides
ms.assetid: b00ab550-5308-4cb8-8330-483cd1d25654
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2611697e479d318245d8306b28c826e744ae85ad
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066849"
---
# <a name="enable-or-disable-a-plan-guide"></a>Включение или отключение структуры плана.
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] отключать и включать руководства планов можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Включить или отключить можно как одно руководство планов, так и все сразу.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Отключение и включение руководств планов с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Попытка удаления или изменения функции, хранимой процедуры или триггера DML, на которые имеется ссылка в структуре плана (как включенных, так и отключенных), приводит к ошибке. Всегда проверяйте зависимости перед удалением или изменением любого из объектов, перечисленных выше.  
  
-   Отключение уже отключенной структуры плана или включение включенной не имеет силы и не вызывает ошибки.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для отключения или включения структуры плана OBJECT необходимо разрешение ALTER для того объекта (например функции, хранимой процедуры), на который ссылается структура плана. Все остальные структуры планов требуют разрешения ALTER DATABASE.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a>Включение или отключение структуры плана  
  
1.  Щелкните значок «+», чтобы развернуть базу данных, в которой требуется включить или отключить структуру плана, затем щелкните значок «+», чтобы развернуть папку **Программирование** .  
  
2.  Щелкните значок «+», чтобы развернуть папку **Структуры планов** .  
  
3.  Правой кнопкой мыши щелкните ту структуру плана, которую требуется включить или отключить, затем выберите команду **Отключить** или **Включить**.  
  
4.  В диалоговом окне **Отключение структуры плана** или **Включение структуры плана** убедитесь, что выбранное действие выполнено успешно, и нажмите кнопку **Закрыть**.  
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a>Отключение или включение всех структур планов в базе данных  
  
1.  Щелкните значок «+», чтобы развернуть базу данных, в которой требуется включить или отключить структуру плана, затем щелкните значок «+», чтобы развернуть папку **Программирование** .  
  
2.  Правой кнопкой мыши щелкните папку **Структуры планов** , после чего выберите команду **Включить все** или **Отключить все**.  
  
3.  В диалоговом окне **Отключение всех структур планов** или **Включение всех структур планов** убедитесь, что выбранное действие выполнено успешно, и нажмите кнопку **Закрыть**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-disable-or-enable-a-plan-guide"></a>Включение или отключение структуры плана  
  
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
  
#### <a name="to-disable-or-enable-all-plan-guides-in-a-database"></a>Отключение или включение всех структур планов в базе данных  
  
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
  
 Дополнительные сведения см. в разделе [sp_control_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).  
  
  

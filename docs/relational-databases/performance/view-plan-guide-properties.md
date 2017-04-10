---
title: "Просмотр свойств структуры плана | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.planguideprop.general.f1"
helpviewer_keywords: 
  - "структуры планов [SQL Server], просмотр свойств структуры плана"
  - "просмотр свойств структуры плана"
ms.assetid: 8c0d2f39-59c1-4168-a649-65473f6a771b
caps.latest.revision: 19
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# Просмотр свойств структуры плана
  Свойства структур планов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно просмотреть при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Просмотр свойств структур планов при помощи различных средств**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Просмотр свойств структуры плана  
  
1.  Щелкните значок «+», чтобы развернуть базу данных, в которой требуется просмотреть свойства структуры планов, после чего щелкните значок «+», чтобы развернуть папку **Программирование** .  
  
2.  Щелкните значок «+», чтобы развернуть папку **Структуры планов** .  
  
3.  Щелкните правой кнопкой мыши структуру плана, свойства которого необходимо просмотреть, и выберите команду **Свойства**.  
  
     Следующие свойства отображаются в диалоговом окне **Свойства структуры плана** .  
  
     **Указания**  
     Отображает указания запросов или план запроса для применения к инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если план запроса задан как указание, отображаются выходные данные инструкции XML Showplan для этого плана.  
  
     **Отключен**  
     Отображает состояние структуры плана. Допустимые значения — **True** и **False**.  
  
     **Название**  
     Отображает имя структуры плана.  
  
     **Параметры**  
     Если тип области равен «SQL» или «TEMPLATE», отображает имя и тип данных для всех параметров, внедренных в инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
     **Поток области**  
     Отображает текст пакета, в котором находится инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
     **Имя объекта области**  
     Если тип области равен «OBJECT», отображает имя хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)], определяемой пользователем скалярной функции, многооператорной возвращающей табличное значение функции или триггера DML, где содержится инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
     **Имя схемы области**  
     Если тип области равен «OBJECT», отображает имя схемы, содержащей объект.  
  
     **Тип области**  
     Отображает тип сущности, в которой присутствует инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)]. Это указывает контекст для сопоставления оператора [!INCLUDE[tsql](../../includes/tsql-md.md)] со структурой плана. Возможными значениями являются **OBJECT**, **SQL**и **TEMPLATE**.  
  
     **Инструкция**  
     Отображает инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], для которой необходимо применить структуру плана.  
  
4.  Нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Просмотр свойств структуры плана  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- If a plan guide named “Guide1” already exists in the AdventureWorks2012 database, delete it.  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID(N'Guide1') IS NOT NULL  
       EXEC sp_control_plan_guide N'DROP', N'Guide1';  
    GO  
    -- creates a plan guide named Guide1 based on a SQL statement  
    EXEC sp_create_plan_guide   
        @name = N'Guide1',   
        @stmt = N'SELECT TOP 1 *   
                  FROM Sales.SalesOrderHeader   
                  ORDER BY OrderDate DESC',   
        @type = N'SQL',  
        @module_or_batch = NULL,   
        @params = NULL,   
        @hints = N'OPTION (MAXDOP 1)';  
    GO  
    -- Gets the name, created date, and all other relevant property information on the plan guide created above.   
    SELECT name AS plan_guide_name,  
       create_date,  
       query_text,  
       scope_type_desc,  
       OBJECT_NAME(scope_object_id) AS scope_object_name,  
       scope_batch,  
       parameters,  
       hints,  
       is_disabled  
    FROM sys.plan_guides  
    WHERE name = N’Guide1’;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sys.plan_guides (Transact-SQL)](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md).  
  
  
---
title: Структуры планов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- SQL plan guides
- OPTIMIZE FOR query hint
- RECOMPILE query hint
- OBJECT plan guide
- plan guides [SQL Server], about plan guides
- OPTION clause
- plan guides [SQL Server]
- USE PLAN query hint
ms.assetid: bfc97632-c14c-4768-9dc5-a9c512f6b2bd
caps.latest.revision: 52
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2e63ff5a6aa32a8db7fb1e11aac6de7966e734a0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34330125"
---
# <a name="plan-guides"></a>Руководства планов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Структуры планов позволяют оптимизировать производительность запросов, если невозможно или нежелательно непосредственно изменять текст фактически имеющегося запроса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Структуры планов влияют на оптимизацию запросов путем присоединения к ним указаний запроса или постоянного плана запроса. Структуры планов полезны, когда небольшое подмножество запросов в приложении базы данных стороннего разработчика выполняются не так, как ожидается. В структуре плана задается инструкция Transact-SQL, которую нужно оптимизировать, и либо предложение OPTION, содержащее указания запросов, либо конкретный план запроса, с помощью которого планируется оптимизировать запрос. При выполнении запроса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляет инструкцию Transact-SQL со структурой плана и присоединяет предложение OPTION к запросу во время выполнения или использует указанный план запроса.  
  
 Общее число структур планов, которые можно создать, ограничивается только доступными системными ресурсами. Тем не менее использование структур планов должно быть ограничено критически важными запросами, затрагиваемыми в целях улучшения или стабилизации производительности. Структуры планов не следует использовать для основной массы запросов развернутого приложения.  
  
> [!NOTE]  
>  Структуру планов можно использовать не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md). Структуры планов видны в любом выпуске. Можно также присоединить базу данных, содержащую структуры планов, к любой версии. Структуры планов остаются нетронутыми при восстановлении или присоединении базы данных к обновленной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="types-of-plan-guides"></a>Типы структур планов  
 Могут быть созданы структуры планов следующих типов.  
  
 ### <a name="object-plan-guide"></a>OBJECT, руководство плана  
 Структура плана OBJECT соответствует запросам, выполняемым в контексте хранимых процедур языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , определяемых пользователем скалярных функций, определяемых пользователем функций с несколькими инструкциями, возвращающих табличные значения, и триггеров DML.  
  
 Предположим, что следующая хранимая процедура, которая принимает параметр `@Country_region`, относится к приложению базы данных, которое развертывается в связи с базой данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
CREATE PROCEDURE Sales.GetSalesOrderByCountry (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h, Sales.Customer AS c,   
        Sales.SalesTerritory AS t  
    WHERE h.CustomerID = c.CustomerID  
        AND c.TerritoryID = t.TerritoryID  
        AND CountryRegionCode = @Country_region  
END;  
```  
  
 Предположим, что эта хранимая процедура была скомпилирована и оптимизирована для `@Country_region = N'AU'` (Австралия). Но из Австралии поступает относительно небольшое количество заказов на продажу, поэтому производительность снижается, если запрос выполняется с использованием значений параметров, относящихся к тем странам, где имеется большее количество заказов на продажу. Так как страна, из которой поступает больше всего заказов на продажу, — США, план запроса, сформированный для значения `@Country_region = N'US'` , вероятно, обеспечит лучшую производительность для всех возможных значений параметра `@Country_region` .  
  
 Чтобы решить эту проблему, измените хранимую процедуру и добавьте указание `OPTIMIZE FOR` в запрос. Однако так как хранимая процедура находится в развернутом приложении, напрямую менять код приложения нельзя. Вместо этого можно создать следующую структуру плана в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```sql  
sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT *FROM Sales.SalesOrderHeader AS h,  
        Sales.Customer AS c,  
        Sales.SalesTerritory AS t  
        WHERE h.CustomerID = c.CustomerID   
            AND c.TerritoryID = t.TerritoryID  
            AND CountryRegionCode = @Country_region',  
@type = N'OBJECT',  
@module_or_batch = N'Sales.GetSalesOrderByCountry',  
@params = NULL,  
@hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
 При выполнении запроса, указанного в инструкции `sp_create_plan_guide` , этот запрос изменяется до оптимизации: в него добавляется предложение `OPTIMIZE FOR (@Country = N''US'')` .  
  
 ### <a name="sql-plan-guide"></a>Структура плана SQL  
 Структура плана SQL соответствует запросам, выполняющимся в контексте изолированных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] и пакетов, не входящих ни в один объект базы данных. Структуры планов SQL также можно использовать для соответствия запросам с параметрами. Структуры планов SQL применяются к изолированным инструкциям [!INCLUDE[tsql](../../includes/tsql-md.md)] и пакетам. Часто эти инструкции передаются приложением с помощью хранимой процедуры [sp_executesql](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) . Например, рассмотрим следующий изолированный пакет:  
  
```sql  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 Чтобы избежать создания параллельного плана выполнения для этого запроса, создайте приведенную ниже структуру плана и присвойте указанию запроса `MAXDOP` значение `1` в параметре `@hints` .  
  
```sql  
sp_create_plan_guide   
@name = N'Guide2',   
@stmt = N'SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC',  
@type = N'SQL',  
@module_or_batch = NULL,   
@params = NULL,   
@hints = N'OPTION (MAXDOP 1)';  
```  
  
> [!IMPORTANT]  
>  Значения, передаваемые для аргументов `@module_or_batch` и `@params` инструкции `sp_create_plan guide` , должны соответствовать тексту настоящего запроса. Дополнительные сведения см. в разделах [sp_create_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md) и [Использование приложения SQL Server Profiler для создания и проверки руководств планов](../../relational-databases/performance/use-sql-server-profiler-to-create-and-test-plan-guides.md).  
  
 Кроме того, структуры планов SQL можно создавать для запросов с той же параметризованной формой, если значением параметра базы данных PARAMETERIZATION является SET или FORCED либо если создана структура плана TEMPLATE, определяющая, что класс запросов должен быть параметризован.  
  
 ### <a name="template-plan-guide"></a>TEMPLATE, структура плана  
 Структура плана TEMPLATE соответствует изолированным инструкциям с параметрами. Эти структуры планов используются для замещения текущего параметра PARAMETERIZATION инструкции SET базы данных для класса запросов.  
  
 Структуры планов TEMPLATE создаются в одной из следующих ситуаций.  
  
-   Параметр базы данных PARAMETERIZATION установлен равным FORCED, но некоторые запросы желательно скомпилировать в соответствии с правилами [простой параметризации](../../relational-databases/query-processing-architecture-guide.md#SimpleParam).  
  
-   Параметр базы данных PARAMETERIZATION установлен равным SIMPLE (значение по умолчанию), но вы хотите включить [принудительную параметризацию](../../relational-databases/query-processing-architecture-guide.md#ForcedParam) для определенного класса запросов.  
  
## <a name="plan-guide-matching-requirements"></a>Требования по соответствию для структур планов  
 Структуры планов действительны в области видимости базы данных, в которой они создаются. Поэтому с запросом могут быть согласованы только структуры планов, находящиеся в базе данных, которая является текущей при выполнении запроса. Например, если [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] является текущей базой данных и выполняется нижеследующий запрос:  
  
 ```sql
 SELECT FirstName, LastName FROM Person.Person;
 ```  
  
 Только руководства планов в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] подлежат сопоставлению с этим запросом. Но если [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] является текущей базой данных и выполняются нижеследующие инструкции:  
  
 ```sql
 USE DB1; 
 SELECT FirstName, LastName FROM Person.Person;
 ```  
  
 Для согласования с запросом применимы только структуры планов в `DB1` , поскольку запрос выполняется в контексте `DB1`.  
  
 В структурах плана, основанных на SQL или TEMPLATE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] посимвольно сравнивает значения аргументов @module_or_batch и @params, переданных в запросе. Это означает, что необходимо предоставить текст точно в том же виде, в каком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получит его в действительном пакете.  
  
 Если @type = 'SQL' и @module_or_batch имеет значение NULL, параметр @module_or_batch получает значение @stmt. Из этого следует, что значение для *statement_text* должно быть предоставлено в идентичном формате, символ к символу, так как оно передается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для упрощения соответствия формата внутренние преобразования не выполняются.  
  
 Если к инструкции могут быть применены и обычная структура плана (SQL или OBJECT), и структура плана TEMPLATE, то используется только обычная структура плана.  
  
> [!NOTE]  
>  Пакет, содержащий инструкцию, для которой необходимо создать структуру плана, не может содержать инструкцию USE *database* .  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a>Влияние структуры плана на кэш планов  
 Создание структуры плана в модуле стирает план запроса для этого модуля из кэша планов. Создание структуры плана типа OBJECT или SQL в потоке стирает план запроса для потока, который имеет такое же значение хеш-функции. Создание структуры плана типа TEMPLATE стирает все потоки с одним оператором из кэша планов через базу данных.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Задача|Раздел|  
|----------|-----------|  
|Описано, как создать структуру плана.|[Создание структуры плана](../../relational-databases/performance/create-a-new-plan-guide.md)|  
|Описано, как создать структуру плана для параметризованных запросов.|[Создание руководства плана для параметризованных запросов](../../relational-databases/performance/create-a-plan-guide-for-parameterized-queries.md)|  
|Описано, как управлять режимом параметризации запроса с использованием структур планов.|[Указание механизма параметризации запросов с помощью структур плана](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)|  
|Описано, как включить постоянный план запроса в структуру плана.|[Применение фиксированного плана запроса к структуре плана](../../relational-databases/performance/apply-a-fixed-query-plan-to-a-plan-guide.md)|  
|Описано, как задать указания запросов в структуре плана.|[Присоединение указаний запросов к структуре плана](../../relational-databases/performance/attach-query-hints-to-a-plan-guide.md)|  
|Описано, как просматривать свойства структуры плана.|[Просмотр свойств структуры плана](../../relational-databases/performance/view-plan-guide-properties.md)|  
|Описано, как использовать профилировщик SQL Server для создания и проверки структур планов.|[Использование приложения SQL Server Profiler для создания и проверки руководств планов](../../relational-databases/performance/use-sql-server-profiler-to-create-and-test-plan-guides.md)|  
|Описано, как проверять структуры планов.|[Проверка руководств плана после обновления](../../relational-databases/performance/validate-plan-guides-after-upgrade.md)|  
  
## <a name="see-also"></a>См. также:  
 [sp_create_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)   
 [sp_control_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)   
 [sys.plan_guides (Transact-SQL)](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [sys.fn_validate_plan_guide (Transact-SQL)](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md)  
  
  

---
title: "В ЧАСОВОМ ПОЯСЕ (Transact-SQL) | Документы Microsoft"
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AT TIME ZONE
- AT_TIME_ZONE_TSQL
helpviewer_keywords: AT TIME ZONE function
ms.assetid: 311f682f-7f1b-43b6-9ea0-24e36b64f73a
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: b9fc240d76c2939e0ed96d87fdbfee35ec8208ce
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="at-time-zone-transact-sql"></a>В ЧАСОВОМ ПОЯСЕ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Преобразует *inputdate* к соответствующим *datetimeoffset* значение в целевой часовой пояс. Если *inputdate* предоставляется без сведения о смещении, функция применяется смещение часового пояса, при условии, что *inputdate* значение указано в целевой часовой пояс. Если *inputdate* предоставляется как *datetimeoffset* значение, чем **AT TIME ZONE** предложение преобразует его в целевой часовой пояс с помощью правил преобразования часового пояса.  
  
 **В ЧАСОВОМ ПОЯСЕ** реализация зависит от Windows механизм для преобразования **datetime** значения в разных часовых поясах.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
inputdate AT TIME ZONE timezone  
```  
  
## <a name="arguments"></a>Аргументы  
 *inputdate*  
 Выражение, которое разрешается к **smalldatetime**, **datetime**, **datetime2**, или **datetimeoffset** значение.  
  
 *timezone*  
 Имя часового пояса назначения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]зависит от часовых поясов, которые хранятся в реестре Windows. Все часовые пояса, установленных на компьютере, хранятся в следующих куст реестра: **KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time зоны**. Список установленных часовые пояса также предоставляются через [sys.time_zone_info &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md) представления.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает тип данных **datetimeoffset**  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Datetimeoffset** значение в целевой часовой пояс.  
  
## <a name="remarks"></a>Remarks  
 **В ЧАСОВОМ ПОЯСЕ** применяет специальные правила для преобразования входных значений в **smalldatetime**, **datetime** и **datetime2** типы данных, которые попадают в интервал, затрагиваемых изменением летнего времени:  
  
-   Если часы имеет значение заранее, то имеется разрыв в формате местного времени, длительность которого зависит от времени взаимных часов (обычно 1 час, но он может быть 30-45 минут, в зависимости от часового пояса). В этом случае при преобразовании моменты времени, принадлежащих пропуска смещение *после* перехода на летнее.  
  
    ```  
    /*  
        Moving to DST in "Central European Standard Time" zone: 
        offset changes from +01:00 -> +02:00   
        Change occurred on March 29th, 2015 at 02:00:00.   
        Adjusted local time became 2015-03-29 03:00:00.  
    */  
    
    --Time before DST change has standard time offset (+01:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T01:01:00', 126)     
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 01:01:00 +01:00   
  
    /*
      Adjusted time from the "gap interval" (between 02:00 and 03:00)
      is moved 1 hour ahead and presented with the summer time offset
      (after the DST change) 
    */
    SELECT CONVERT(datetime2(0), '2015-03-29T02:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00
      
    --Time after 03:00 is presented with the summer time offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T03:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00  
  
    ```  
  
- Если снова установить часы 2 часа местного времени перекрываются на один час.  В этом случае выводится моменты времени, принадлежащих перекрывающихся интервал смещения *перед* внесения изменений:  
  
    ```  
    /*  
        Moving back from DST to standard time in 
        "Central European Standard Time" zone: 
        offset changes from +02:00 -> +01:00.  
        Change occurred on October 25th, 2015 at 03:00:00.   
        Adjusted local time became 2015-10-25 02:00:00   
    */  
    
    --Time before the change has DST offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-10-25T01:01:00', 126)      
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 01:01:00 +02:00  
    
    /*
      Time from the "overlapped interval" is presented with standard time 
      offset (before the change)    
    */
    SELECT CONVERT(datetime2(0), '2015-10-25T02:00:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 02:00:00 +02:00  
    
    
    --Time after 03:00 is regularly presented with the standard time offset (+01:00)    
    SELECT CONVERT(datetime2(0), '2015-10-25T03:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 03:01:00 +01:00
  
    ```  

Так как некоторые сведения (такие как правила часового пояса) хранятся вне [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и подлежат случайные изменения **AT TIME ZONE** классифицированы как недетерминированные функции. 
  
## <a name="examples"></a>Примеры  
  
### <a name="a-add-target-time-zone-offset-to-datetime-without-offset-information"></a>A. Добавить смещение часового пояса целевого даты и времени без смещения информации  
 Используйте **AT TIME ZONE** добавить смещение, на основании правил часового пояса, если известно, что исходный **datetime** значения приведены в том же часовом поясе:  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="b-convert-values-between-different-time-zones"></a>Б. Преобразовывать значения из разных часовых поясах  
 В следующем примере преобразование значений между различными часовыми поясами:  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST,  
    OrderDate AT TIME ZONE 'Pacific Standard Time'   
    AT TIME ZONE 'Central European Standard Time' AS OrderDate_TimeZoneCET  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="c-query-temporal-tables-using-local-time-zone"></a>В. Запрос Темпоральных таблиц с использованием местного часового пояса  
 В приведенном ниже примере выбирает данные из временной таблицы.  
  
```  
USE AdventureWorks2016;  
GO  
  
DECLARE @ASOF datetimeoffset;  
SET @ASOF = DATEADD (month, -1, GETDATE()) AT TIME ZONE 'UTC';  
  
-- Query state of the table a month ago projecting period   
-- columns as Pacific Standard Time  
SELECT BusinessEntityID, PersonType, NameStyle, Title,   
    FirstName, MiddleName,  
    ValidFrom AT TIME ZONE 'Pacific Standard Time' 
FROM  Person.Person_Temporal  
FOR SYSTEM_TIME AS OF @ASOF;  
```  
  
## <a name="see-also"></a>См. также  
 [Типы даты и времени](../../t-sql/data-types/date-and-time-types.md)   
 [Данных даты и времени типы и функции &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  
  

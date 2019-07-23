---
title: AT TIME ZONE (Transact-SQL) | Документы Майкрософт
ms.date: 06/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.custom: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AT TIME ZONE
- AT_TIME_ZONE_TSQL
helpviewer_keywords:
- AT TIME ZONE function
ms.assetid: 311f682f-7f1b-43b6-9ea0-24e36b64f73a
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current||=azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: ff3d3db1ab4fc3d02e8710cf482225523285c0a0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031521"
---
# <a name="at-time-zone-transact-sql"></a>AT TIME ZONE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Преобразует аргумент *inputdate* в соответствующее значение *datetimeoffset* в целевом часовом поясе. Если аргумент *inputdate* предоставляется без сведений о смещении, функция применяет смещение часового пояса, предполагая, что *inputdate* находится в целевом часовом поясе. Если аргумент *inputdate* предоставляется как значение *datetimeoffset*, предложение **AT TIME ZONE** преобразует его в целевой часовой пояс с помощью правил преобразования часовых поясов.  
  
 При преобразовании значений **datetime** в разных часовых поясах реализация функции **AT TIME ZON** зависит от механизма Windows.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
inputdate AT TIME ZONE timezone  
```  
  
## <a name="arguments"></a>Аргументы  
 *inputdate*  
 Выражение, которое можно привести к значению **smalldatetime**, **datetime**, **datetime2** или **datetimeoffset**.  
  
 *timezone*  
 Имя целевого часового пояса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зависит от часовых поясов, которые хранятся в реестре Windows. Часовые пояса, установленные на компьютере, хранятся в следующем кусте реестра: **KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones**. Список установленных часовых поясов также отображается в представлении [sys.time_zone_info (Transact-SQL)](../../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает тип данных **datetimeoffset**.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **datetimeoffset** в целевом часовом поясе.  
  
## <a name="remarks"></a>Remarks  
 **AT TIME ZONE** применяет специальные правила для преобразования входных значений с типами данных **smalldatetime**, **datetime** и **datetime2**, которые попадают в период перехода на летнее время:  
  
-   Если часы переводятся вперед, возникает разница с местным временем, равная интервалу перевода. Интервал обычно составляет 1 час, но в некоторых часовых поясах это может быть 30–45 минут. Точки во времени, попадающие в указанный период, преобразуются со смещением *после* перехода на летнее время.  
  
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
  
- Если время переводится назад, 2 часа местного времени перекрываются на один час.  В этом случае точки во времени, входящие в перекрывающийся интервал, представляются со смещением *после* изменения времени.  
  
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

Так как некоторые сведения (например, правила часовых поясов) хранятся вне [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и могут иногда меняться, функция **AT TIME ZONE** классифицируется как недетерминированная. 
  
## <a name="examples"></a>Примеры  
  
### <a name="a-add-target-time-zone-offset-to-datetime-without-offset-information"></a>A. Добавление смещения часового пояса к datetime без сведений о смещении  
 Используйте функцию **AT TIME ZONE**, чтобы добавить смещение на основании правил для часовых поясов, если известно, что исходные значения **datetime** указаны в том же часовом поясе:  
  
```sql
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="b-convert-values-between-different-time-zones"></a>Б. Преобразование значений между разными часовыми поясами  
 В следующем примере показано преобразование значений между разными часовыми поясами:  
  
```sql
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST,  
    OrderDate AT TIME ZONE 'Central European Standard Time' AS OrderDate_TimeZoneCET  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="c-query-temporal-tables-using-local-time-zone"></a>В. Запрос темпоральных таблиц с использованием местного часового пояса  
 В приведенном ниже примере показан выбор данных из темпоральной таблицы.  
  
```sql
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
  
## <a name="see-also"></a>См. также:  
 [Типы даты и времени](../../t-sql/data-types/date-and-time-types.md)   
 [Типы данных и функции даты и времени (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  

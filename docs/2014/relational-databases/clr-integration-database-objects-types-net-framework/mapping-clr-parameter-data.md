---
title: Сопоставление данных параметров среды CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 17eeefbe125722c666f9f56394028da8c66a66b3
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75232281"
---
# <a name="mapping-clr-parameter-data"></a>Сопоставление данных о параметрах CLR
  В следующей таблице перечислены [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных, их эквиваленты в среде CLR для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в `System.Data.SqlTypes` пространстве имен и их собственные эквиваленты в среде CLR в [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
||||  
|-|-|-|  
|**Типы данных SQL Server**|Тип (в System.Data.SqlTypes or Microsoft.SqlServer.Types)|**Тип данных среды CLR (.NET Framework)**|  
|`bigint`|`SqlInt64`|**Int64, Nullable\<Int64>**|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|**Логическое значение,\<допускающее значение NULL>**|  
|`char`|Нет|Нет|  
|`cursor`|Нет|Нет|  
|`date`|`SqlDateTime`|**DateTime, Nullable\<DateTime>**|  
|`datetime`|`SqlDateTime`|**DateTime, Nullable\<DateTime>**|  
|`datetime2`|Нет|**DateTime, Nullable\<DateTime>**|  
|`DATETIMEOFFSET`|`None`|**DateTimeOffset, Nullable\<>DateTimeOffset**|  
|`decimal`|`SqlDecimal`|**Десятичный,\<допускающий значения NULL>**|  
|`float`|`SqlDouble`|**Double, допускающий значение NULL\<Double>**|  
|`geography`|`SqlGeography`<br /><br /> `SqlGeography`определяется в Microsoft. SqlServer. types. dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=53164).|Нет|  
|`geometry`|`SqlGeometry`<br /><br /> `SqlGeometry`определяется в Microsoft. SqlServer. types. dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=53164).|Нет|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> `SqlHierarchyId`определяется в Microsoft. SqlServer. types. dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=53164).|Нет|  
|`image`|Нет|Нет|  
|`int`|`SqlInt32`|**Int32,>\<Nullable Int32**|  
|`money`|`SqlMoney`|**Десятичный,\<допускающий значения NULL>**|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|Нет|Нет|  
|`numeric`|`SqlDecimal`|**Десятичный,\<допускающий значения NULL>**|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> 
  `SQLChars` лучше подходит для передачи данных и доступа, тогда как `SQLString` более подходит для выполнения строковых операций.|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|**Char, String, char [], Nullable\<char>**|  
|`real`|
  `SqlSingle` (но `SqlSingle` поддерживает больший диапазон значений, чем `real`)|**Single, только\<одиночный>, допускающий значение null**|  
|`rowversion`|Нет|`Byte[]`|  
|`smallint`|`SqlInt16`|**Int16, Nullable\<>обнуляемого типа**|  
|`smallmoney`|`SqlMoney`|**Десятичный,\<допускающий значения NULL>**|  
|`sql_variant`|Нет|`Object`|  
|`table`|Нет|Нет|  
|`text`|Нет|Нет|  
|`time`|Нет|**TimeSpan, Nullable\<TimeSpan>**|  
|`timestamp`|Нет|Нет|  
|`tinyint`|`SqlByte`|**Byte, допускающий значение NULL\<байт>**|  
|`uniqueidentifier`|`SqlGuid`|**GUID, GUID\<, допускающий значение NULL>**|  
|`User-defined type(UDT)`|Нет|Тот же класс связывается с определяемым пользователем типом данных в той же сборке или в зависимой сборке.|  
|**varbinary**|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|**Byte, Byte [], допускающий значение NULL\<байт>**|  
|`varchar`|Нет|Нет|  
|`xml`|`SqlXml`|Нет|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Автоматическое преобразование типов данных для выходных параметров  
 Метод CLR может возвращать данные вызывающему коду или программе, сопровождая входной параметр модификатором `out` (Microsoft Visual C#) или `<Out()> ByRef` (Microsoft Visual Basic). Если входной параметр принадлежит типу данных CLR в пространстве имен `System.Data.SqlTypes`, и вызывающая программа указывает свой соответствующий тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как входной параметр, преобразование типов осуществляется автоматически, когда метод CLR возвращает тип данных.  
  
 Так, следующая хранимая процедура CLR имеет входной параметр с типом данных CLR `SqlInt32`, помеченный модификатором `out` (C#) или `<Out()> ByRef` (Visual Basic):  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 После формирования сборки в базе данных хранимая процедура создается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со следующим кодом Transact-SQL, который указывает тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`int` для параметра OUTPUT:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 При вызове хранимой процедуры CLR тип данных `SqlInt32` автоматически преобразуется в тип данных `int` и возвращается вызывающей программе.  
  
 Однако не все типы данных CLR могут автоматически преобразовываться в эквивалентные им типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью выходного параметра. В следующей таблице перечислены эти исключения.  
  
|||  
|-|-|  
|**Тип данных CLR (SQL Server)**|**Типы данных SQL Server**|  
|`Decimal`|smallmoney|  
|`SqlMoney`|smallmoney|  
|`Decimal`|money|  
|`DateTime`|smalldatetime|  
|`SQLDateTime`|smalldatetime|  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|В таблицу сопоставления добавлены типы `SqlGeography`, `SqlGeometry` и `SqlHierarchyId`.|  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  

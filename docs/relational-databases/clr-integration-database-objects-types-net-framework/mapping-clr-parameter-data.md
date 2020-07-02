---
title: Сопоставление данных параметров среды CLR | Документация Майкрософт
description: В этой статье перечислены Microsoft SQL Server типы данных, эквиваленты в CLR для SQL Server и собственные эквиваленты CLR в .NET Framework.
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
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
ms.openlocfilehash: 911b56023ea78ec75e605a39a39b705724101dee
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719940"
---
# <a name="mapping-clr-parameter-data"></a>Сопоставление данных о параметрах CLR
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В следующей таблице перечислены [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных, их эквиваленты в среде CLR для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в пространстве имен **System. Data. SqlTypes** и их собственные эквиваленты в среде CLR в [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
||||  
|-|-|-|  
|**Тип данных SQL Server**|Тип (в System.Data.SqlTypes or Microsoft.SqlServer.Types)|**Тип данных среды CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64>**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**bit**|**SqlBoolean**|**Логическое значение, допускающее значение null\<Boolean>**|  
|**char**|Отсутствуют|Отсутствуют|  
|**курсор**|Отсутствуют|Отсутствуют|  
|**date**|**SqlDateTime**|**DateTime, Nullable\<DateTime>**|  
|**datetime**|**SqlDateTime**|**DateTime, Nullable\<DateTime>**|  
|**datetime2**|Отсутствуют|**DateTime, Nullable\<DateTime>**|  
|**DATETIMEOFFSET**|**None**|**DateTimeOffset, Nullable\<DateTimeOffset>**|  
|**decimal**|**SqlDecimal**|**Decimal, допускающий значения NULL\<Decimal>**|  
|**float**|**SqlDouble**|**Double, null\<Double>**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** определяется в Microsoft.SqlServer.Types.dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|Отсутствуют|  
|**объект**|**SqlGeometry**<br /><br /> **SqlGeometry** определяется в Microsoft.SqlServer.Types.dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|Отсутствуют|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **Метод SqlHierarchyId** определяется в Microsoft.SqlServer.Types.dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|Отсутствуют|  
|**изображение**|Отсутствуют|Отсутствуют|  
|**int**|**SqlInt32**|**Int32, Nullable\<Int32>**|  
|**money**|**SqlMoney**|**Decimal, допускающий значения NULL\<Decimal>**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|Отсутствуют|Отсутствуют|  
|**numeric**|**SqlDecimal**|**Decimal, допускающий значения NULL\<Decimal>**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SqlChars** лучше подходит для обмена данными и доступа, а **SqlString** — более подходящие для выполнения строковых операций.|**String, Char[]**|  
|**nvarchar (1), nchar (1)**|**SqlChars, SqlString**|**Char, String, char [], Nullable\<char>**|  
|**real**|**Склсингле** (диапазон **склсингле**, но больше **вещественного**)|**Single, допускающий значения NULL\<Single>**|  
|**rowversion**|Отсутствуют|**Byte []**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16>**|  
|**smallmoney**|**SqlMoney**|**Decimal, допускающий значения NULL\<Decimal>**|  
|**sql_variant**|Отсутствуют|**Объект**|  
|**table**|Отсутствуют|Отсутствуют|  
|**text**|Отсутствуют|Отсутствуют|  
|**time**|Отсутствуют|**TimeSpan, Nullable\<TimeSpan>**|  
|**timestamp**|Отсутствуют|Отсутствуют|  
|**tinyint**|**SqlByte**|**Byte, допускает значение null\<Byte>**|  
|**uniqueidentifier**|**склгуид**|**GUID, допускающий значение null\<Guid>**|  
|**Определяемый пользователем тип (UDT)**|Отсутствуют|Тот же класс связывается с определяемым пользователем типом данных в той же сборке или в зависимой сборке.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**varbinary (1), binary (1)**|**SqlBytes, SqlBinary**|**Byte, Byte [], допускающий значения NULL\<byte>**|  
|**varchar**|Отсутствуют|Отсутствуют|  
|**xml**|**SqlXml**|Отсутствуют|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Автоматическое преобразование типов данных для выходных параметров  
 Метод CLR может возвращать сведения вызывающему коду или программе путем пометки входного параметра модификатором **out** (Microsoft Visual C#) или ** \<Out()> ByRef** (Microsoft Visual Basic), если входной параметр является типом данных CLR в системе. пространство имен **Data. SqlTypes** и вызывающая программа указывает его эквивалентный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных в качестве входного параметра. преобразование типа происходит автоматически, когда метод CLR возвращает тип данных.  
  
 Например, следующая хранимая процедура CLR имеет входной параметр типа данных **SqlInt32** CLR, который помечен как **out** (C#) или ** \<Out()> ByRef** (Visual Basic):  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 После построения и создания сборки в базе данных хранимая процедура создается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью следующего Transact-SQL, который задает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных **int** в качестве выходного параметра:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 При вызове хранимой процедуры CLR тип данных **SqlInt32** автоматически преобразуется в тип данных **int** и возвращается вызывающей программе.  
  
 Однако не все типы данных CLR могут автоматически преобразовываться в эквивалентные им типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью выходного параметра. В следующей таблице перечислены эти исключения.  
  
|||  
|-|-|  
|**Тип данных CLR (SQL Server)**|**Тип данных SQL Server**|  
|**Decimal**|smallmoney|  
|**SqlMoney**|smallmoney|  
|**Decimal**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|В таблицу сопоставления добавлены типы **SqlGeography**, **SqlGeometry**и **метод SqlHierarchyId** .|  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  

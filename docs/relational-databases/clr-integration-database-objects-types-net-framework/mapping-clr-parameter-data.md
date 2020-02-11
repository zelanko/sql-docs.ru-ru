---
title: Сопоставление данных параметров среды CLR | Документация Майкрософт
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
ms.openlocfilehash: 530db4d31d3db4773713816f1b68404990997512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081316"
---
# <a name="mapping-clr-parameter-data"></a>Сопоставление данных о параметрах CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В следующей таблице перечислены [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных, их эквиваленты в среде CLR для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в пространстве имен **System. Data. SqlTypes** и их собственные эквиваленты в среде CLR в [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
||||  
|-|-|-|  
|**Тип данных SQL Server**|Тип (в System.Data.SqlTypes or Microsoft.SqlServer.Types)|**Тип данных среды CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64>**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**bit**|**SqlBoolean**|**Логическое значение,\<допускающее значение NULL>**|  
|**типа**|None|None|  
|**набора**|None|None|  
|**date**|**SqlDateTime**|**DateTime, Nullable\<DateTime>**|  
|**datetime**|**SqlDateTime**|**DateTime, Nullable\<DateTime>**|  
|**datetime2**|None|**DateTime, Nullable\<DateTime>**|  
|**DATETIMEOFFSET**|**None**|**DateTimeOffset, Nullable\<>DateTimeOffset**|  
|**Decimal**|**SqlDecimal**|**Десятичный,\<допускающий значения NULL>**|  
|**float**|**SqlDouble**|**Double, допускающий значение NULL\<Double>**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** определяется в Microsoft. SqlServer. types. dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** определяется в Microsoft. SqlServer. types. dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**hierarchyid**|**Метод SqlHierarchyId**<br /><br /> **Метод SqlHierarchyId** определяется в Microsoft. SqlServer. types. dll, который устанавливается вместе с SQL Server и может быть скачан из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**Эскиз**|None|None|  
|**int**|**SqlInt32**|**Int32,>\<Nullable Int32**|  
|**money**|**SqlMoney**|**Десятичный,\<допускающий значения NULL>**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|None|None|  
|**ISNUMERIC**|**SqlDecimal**|**Десятичный,\<допускающий значения NULL>**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SqlChars** лучше подходит для обмена данными и доступа, а **SqlString** — более подходящие для выполнения строковых операций.|**String, Char[]**|  
|**nvarchar (1), nchar (1)**|**SqlChars, SqlString**|**Char, String, char [], Nullable\<char>**|  
|**Real**|**Склсингле** (диапазон **склсингле**, но больше **вещественного**)|**Single, только\<одиночный>, допускающий значение null**|  
|**rowversion**|None|**Byte []**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<>обнуляемого типа**|  
|**smallmoney**|**SqlMoney**|**Десятичный,\<допускающий значения NULL>**|  
|**sql_variant**|None|**Объект**|  
|**Таблица**|None|None|  
|**полнотекстовым**|None|None|  
|**time**|None|**TimeSpan, Nullable\<TimeSpan>**|  
|**TIMESTAMP**|None|None|  
|**tinyint**|**склбите**|**Byte, допускающий значение NULL\<байт>**|  
|**UNIQUEIDENTIFIER**|**склгуид**|**GUID, GUID\<, допускающий значение NULL>**|  
|**Определяемый пользователем тип (UDT)**|None|Тот же класс связывается с определяемым пользователем типом данных в той же сборке или в зависимой сборке.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**varbinary (1), binary (1)**|**SqlBytes, SqlBinary**|**Byte, Byte [], допускающий значение NULL\<байт>**|  
|**varchar**|None|None|  
|**xml**|**SqlXml**|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Автоматическое преобразование типов данных для выходных параметров  
 Метод CLR может возвращать сведения вызывающему коду или программе путем пометки входного параметра модификатором **out** (Microsoft Visual C#) или ** \<out () > ByRef** (Microsoft Visual Basic), если входной параметр является типом данных CLR в системе. пространство имен **Data. SqlTypes** и вызывающая программа указывает его эквивалентный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных в качестве входного параметра. преобразование типа происходит автоматически, когда метод CLR возвращает тип данных.  
  
 Например, следующая хранимая процедура CLR имеет входной параметр типа данных **SqlInt32** CLR, который помечен как **out** (C#) или ** \<out () > ByRef** (Visual Basic):  
  
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
  
 После построения и создания сборки в базе данных хранимая процедура создается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью следующего TRANSACT-SQL, который задает тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных **int** в качестве выходного параметра:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 При вызове хранимой процедуры CLR тип данных **SqlInt32** автоматически преобразуется в тип данных **int** и возвращается вызывающей программе.  
  
 Однако не все типы данных CLR могут автоматически преобразовываться в эквивалентные им типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью выходного параметра. В следующей таблице перечислены эти исключения.  
  
|||  
|-|-|  
|**Тип данных CLR (SQL Server)**|**Тип данных SQL Server**|  
|**Десятич**|smallmoney|  
|**SqlMoney**|smallmoney|  
|**Десятич**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|В таблицу сопоставления добавлены типы **SqlGeography**, **SqlGeometry**и **метод SqlHierarchyId** .|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  

---
title: "Сопоставление данных о параметрах CLR | Документы Microsoft"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "71"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3592a4c547b3586df4be45b2e1734e330dd16664
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mapping-clr-parameter-data"></a>Сопоставление данных о параметрах CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В следующей таблице перечислены [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , типы данных эквивалентов в среде (CLR) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в **System.Data.SqlTypes** пространства имен и их собственные эквиваленты CLR в [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET framework.  
  
||||  
|-|-|-|  
|**Тип данных SQL Server**|Тип (в System.Data.SqlTypes or Microsoft.SqlServer.Types)|**Тип данных CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, допускающие значения NULL\<Int64 >**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte]**|  
|**bit**|**SqlBoolean**|**Логический, допускающие значения NULL\<логическое >**|  
|**char**|None|None|  
|**курсор**|None|None|  
|**date**|**SqlDateTime**|**DateTime, допускающий значение NULL\<DateTime >**|  
|**datetime**|**SqlDateTime**|**DateTime, допускающий значение NULL\<DateTime >**|  
|**datetime2**|None|**DateTime, допускающий значение NULL\<DateTime >**|  
|**DATETIMEOFFSET**|**None**|**DateTimeOffset, допускающие значения NULL\<DateTimeOffset >**|  
|**decimal**|**SqlDecimal**|**Decimal, допускающий значение NULL\<десятичное число >**|  
|**float**|**SqlDouble**|**Двойное, допускающие значения NULL\<Double >**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** определяется в Microsoft.SqlServer.Types.dll, которая устанавливается вместе с SQL Server и могут быть загружены из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** определяется в Microsoft.SqlServer.Types.dll, которая устанавливается вместе с SQL Server и могут быть загружены из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** определяется в Microsoft.SqlServer.Types.dll, которая устанавливается вместе с SQL Server и могут быть загружены из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**image**|None|None|  
|**int**|**SqlInt32**|**Int32, допускающие значения NULL\<Int32 >**|  
|**money**|**SqlMoney**|**Decimal, допускающий значение NULL\<десятичное число >**|  
|**nchar**|**SqlChars SqlString**|**Строка, Char]**|  
|**ntext**|None|None|  
|**numeric**|**SqlDecimal**|**Decimal, допускающий значение NULL\<десятичное число >**|  
|**nvarchar**|**SqlChars SqlString**<br /><br /> **SQLChars** лучше подходит для передачи данных и доступа, и **SQLString** лучше подходит для выполнения строковых операций.|**Строка, Char]**|  
|**nvarchar(1), nchar(1)**|**SqlChars SqlString**|**Char, строки, Char [], Nullable\<char >**|  
|**real**|**SqlSingle** (диапазон **SqlSingle**, однако больше, чем **реальные**)|**Единый, допускающие значения NULL\<один >**|  
|**rowversion**|None|**Byte]**|  
|**smallint**|**SqlInt16**|**Int16, допускающие значения NULL\<Int16 >**|  
|**smallmoney**|**SqlMoney**|**Decimal, допускающий значение NULL\<десятичное число >**|  
|**sql_variant**|None|**Объект**|  
|**table**|None|None|  
|**text**|None|None|  
|**time**|None|**Интервал времени, допускающие значения NULL\<TimeSpan >**|  
|**timestamp**|None|None|  
|**tinyint**|**SqlByte**|**Байт, допускающий значение NULL\<байтов >**|  
|**uniqueidentifier**|**SqlGuid**|**Идентификатор GUID, допускающих значение NULL\<Guid >**|  
|**Определяемые пользователем type(UDT)**|None|Тот же класс связывается с определяемым пользователем типом данных в той же сборке или в зависимой сборке.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte]**|  
|**varbinary(1), binary(1)**|**SqlBytes, SqlBinary**|**байт, Byte [], Nullable\<байтов >**|  
|**varchar**|None|None|  
|**xml**|**SqlXml**|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Автоматическое преобразование типов данных для выходных параметров  
 Метод CLR может возвращать данные вызывающему коду или программы, помечая входной параметр с **out** модификатор (Microsoft Visual C#) или  **\<Out() > ByRef** (Microsoft Visual Basic) Если входной параметр имеет тип данных CLR в **System.Data.SqlTypes** пространства имен и вызывающая программа указывает эквивалентное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как входной параметр типа данных, преобразование типов осуществляется автоматически Когда метод CLR возвращает тип данных.  
  
 Например, следующая хранимая процедура CLR имеет входной параметр **SqlInt32** типа данных CLR, который отмечен атрибутом **out** (C#) или  **\<Out() > ByRef** () Visual Basic):  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ … }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
…  
End Sub  
```  
  
 После сборки построен и в базе данных, хранимая процедура создается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следующий запрос Transact-SQL, который указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных **int** как ВЫХОДНОЙ параметр:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Когда хранимая CLR вызывается процедура, **SqlInt32** автоматически преобразуется в тип данных **int** тип данных и возвращается вызывающей программе.  
  
 Однако не все типы данных CLR могут автоматически преобразовываться в эквивалентные им типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью выходного параметра. В следующей таблице перечислены эти исключения.  
  
|||  
|-|-|  
|**Тип данных CLR (SQL Server)**|**Тип данных SQL Server**|  
|**Десятичное число**|SMALLMONEY|  
|**SqlMoney**|SMALLMONEY|  
|**Десятичное число**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Добавлен **SqlGeography**, **SqlGeometry**, и **SqlHierarchyId** типов в таблицу сопоставления.|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  

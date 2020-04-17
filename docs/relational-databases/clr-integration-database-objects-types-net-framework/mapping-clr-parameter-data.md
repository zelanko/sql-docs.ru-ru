---
title: Картирование данных параметров CLR (ru) Документы Майкрософт
description: В этой статье перечислены типы данных сервера Microsoft S'L Server, эквиваленты в CLR для сервера S'L и нативные эквиваленты CLR в рамочной программе .NET.
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
ms.openlocfilehash: 360a94229b107e9f24bb2a769157c75cdeb3c143
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488477"
---
# <a name="mapping-clr-parameter-data"></a>Сопоставление данных о параметрах CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В следующей [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблице перечислены типы данных, их эквиваленты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в общем времени выполнения языка (CLR) в пространстве имен [!INCLUDE[msCoName](../../includes/msconame-md.md)] **System.Data.SqlTypes** и их родные эквиваленты CLR в рамочном выражении .NET.  
  
||||  
|-|-|-|  
|**Тип данных SQL Server**|Тип (в System.Data.SqlTypes or Microsoft.SqlServer.Types)|**Тип данных среды CLR (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64>**|  
|**binary**|**SqlBytes, SqlBinary**|**Байт**|  
|**bit**|**SqlBoolean**|**Булеан,\<Nullable Boolean>**|  
|**char**|None|None|  
|**курсор**|None|None|  
|**date**|**SqlDateTime**|**DateTime, Nullable\<DateTime>**|  
|**datetime**|**SqlDateTime**|**DateTime, Nullable\<DateTime>**|  
|**datetime2**|None|**DateTime, Nullable\<DateTime>**|  
|**Datetimeoffset**|**Нет**|**DateTimeOffset, Nullable\<DateTimeOffset>**|  
|**decimal**|**SqlDecimal**|**Десятичная, необслуживаемая\<десятичная>**|  
|**float**|**SqlDouble**|**Двойной,\<nullable Двойной>**|  
|**География**|**SqlGeography**<br /><br /> **SqlGeography** определяется в Microsoft.SqlServer.Types.dll, которая устанавливается с помощью [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] сервера S'L и может быть загружена из [пакета функций.](https://www.microsoft.com/download/details.aspx?id=52676)|None|  
|**Геометрии**|**SqlGeometry**<br /><br /> **СклГеометрия** определяется в Microsoft.SqlServer.Types.dll, которая устанавливается с помощью [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] сервера S'L и может быть загружена из [пакета функций.](https://www.microsoft.com/download/details.aspx?id=52676)|None|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** определяется в Microsoft.SqlServer.Types.dll, который устанавливается с помощью [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] сервера S'L и может быть загружен из [пакета функций.](https://www.microsoft.com/download/details.aspx?id=52676)|None|  
|**image**|None|None|  
|**int**|**SqlInt32**|**Int32, Nullable\<Int32>**|  
|**money**|**SqlДеньги**|**Десятичная, необслуживаемая\<десятичная>**|  
|**nchar**|**SqlChars, SqlString**|**Струна, Чаре**|  
|**ntext**|None|None|  
|**numeric**|**SqlDecimal**|**Десятичная, необслуживаемая\<десятичная>**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **S'LChars** лучше подходит для передачи данных и доступа, а **S'LString** лучше подходит для выполнения операций строки.|**Струна, Чаре**|  
|**nvarchar (1), nchar(1)**|**SqlChars, SqlString**|**Чар, Струна, Чаре,\<Nullable char>**|  
|**real**|**SqlSingle** (диапазон **SqlSingle**, однако, больше, чем **реальные**)|**Одноместный,\<недействительный сингл>**|  
|**rowversion**|None|**Байт**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16>**|  
|**smallmoney**|**SqlДеньги**|**Десятичная, необслуживаемая\<десятичная>**|  
|**sql_variant**|None|**Объект**|  
|**table**|None|None|  
|**text**|None|None|  
|**time**|None|**TimeSpan, Nullable\<TimeSpan>**|  
|**timestamp**|None|None|  
|**tinyint**|**SqlByte**|**Байт, Nullable\<Байт>**|  
|**uniqueidentifier**|**SqlGuid**|**Гид, Nullable\<Guid>**|  
|**Тип, определяемый пользователем (UDT)**|None|Тот же класс связывается с определяемым пользователем типом данных в той же сборке или в зависимой сборке.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Байт**|  
|**варбинар (1), двоичный(1)**|**SqlBytes, SqlBinary**|**байт, Байт, Nullable\<байт>**|  
|**varchar**|None|None|  
|**xml**|**Sqlxml**|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Автоматическое преобразование типов данных для выходных параметров  
 Метод CLR может вернуть информацию в код вызова или программу, пометив вхотливый параметр с измодизатором **out** (Microsoft Visual C) или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ** \<Out()> ByRef** (Microsoft Visual Basic) Если входним параметром является тип данных CLR в пространстве имен **System.Data.SqlTypes,** а программа вызова определяет свой эквивалентный тип данных в качестве вхонного параметра, то при автоматическом возврате типа типа clR происходит преобразование типа.  
  
 Например, следующая процедура хранения CLR имеет параметр ввода типа данных **SqlInt32** CLR, который отмечен **из** (C) или ** \<Out()> ByRef** (Visual Basic):  
  
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
  
 После сборки, построенной и создаваемой в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных, процедура хранения создается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следующем Transact-S'L, который определяет тип индификации данных **в** качестве параметра OUTPUT:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Когда процедура хранения CLR называется, тип данных **SqlInt32** автоматически преобразуется в тип данных **int** и возвращается в программу вызова.  
  
 Однако не все типы данных CLR могут автоматически преобразовываться в эквивалентные им типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью выходного параметра. В следующей таблице перечислены эти исключения.  
  
|||  
|-|-|  
|**Тип данных CLR (SQL Server)**|**Тип данных SQL Server**|  
|**Decimal**|smallmoney|  
|**SqlДеньги**|smallmoney|  
|**Decimal**|money|  
|**Дата и время**|smalldatetime|  
|**СЗЛДатЕТайм**|smalldatetime|  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Добавлены типы **SqlGeography,** **SqlGeometry**и **SqlHierarchyId** в таблицу отображения.|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  

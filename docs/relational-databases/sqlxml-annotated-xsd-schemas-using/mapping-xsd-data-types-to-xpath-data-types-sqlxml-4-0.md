---
title: Сопоставление типов данных XSD с типами данных XPath (SQLXML)
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6b956bf3a52b9ae14e59af770d279e8be8fec028
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257378"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Сопоставление типов данных XSD с типами данных XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  При выполнении запроса XPath к схеме XSD и указании типа XSD в атрибуте **xsd: Type** XPath использует тип данных, указанный при обработке запроса.  
  
 Тип данных XPath для узла выводится из типа данных XSD в схеме, как показано в следующей таблице. (Узел EmployeeID используется в демонстрационных целях.)  
  
|Тип данных XSD|Тип данных XDR|Эквивалентный<br /><br /> тип данных XPath|SQL Server<br /><br /> преобразование не используется|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **HexBinary**|**None**<br /><br /> **bin. base64bin. hex**|**Неприменимо**|Нет<br /><br /> EmployeeID|  
|**Логический**|**логическая**|**логическая**|CONVERT(bit, EmployeeID)|  
|**Decimal, Integer, float, Byte, Short, int, Long, float, Double, Унсигнедбите, Унсигнедшорт, unsignedInt, Унсигнедлонг**|**number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8**|**Нумерация**|CONVERT(float(53), EmployeeID)|  
|**ID, IDREF, идрефсентити, сущности, нотация, NMTOKEN, NMTOKENS, DateTime, String, AnyURI**|**ID, IDREF, идрефсентити, сущности, перечисление, нотация, NMTOKEN, NMTOKENS, char, dateTime, dateTime.tz, String, URI, UUID**|**Строка**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**decimal**|**fixed14.4**|**Неприменимо (в XPath отсутствует тип данных, эквивалентный фиксированному типу данных XDR 14,4.)**|CONVERT(money, EmployeeID)|  
|**Дата**|**Дата**|**Строка**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**Таймаут**|**Таймаут**<br /><br /> **time.tz**|**Строка**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  

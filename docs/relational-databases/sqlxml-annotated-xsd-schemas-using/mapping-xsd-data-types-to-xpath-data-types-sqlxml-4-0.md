---
title: Сопоставление типов данных XSD с типами данных XPath (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f10134d4aa4d71c4471e5e3120b3f8fbd8ee1748
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980783"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Сопоставление типов данных XSD с типами данных XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  При выполнении запроса XPath к схеме XSD и тип XSD задан в **заметки xsd: Type** атрибут, XPath использует тип данных, указанный при обработке запроса.  
  
 Тип данных XPath для узла выводится из типа данных XSD в схеме, как показано в следующей таблице. (Узел EmployeeID используется в демонстрационных целях.)  
  
|Тип данных XSD|Тип данных XDR|Эквивалентный<br /><br /> тип данных XPath|SQL Server<br /><br /> преобразование не используется|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **hexBinary**|**None**<br /><br /> **bin.base64bin.hex**|**Неприменимо**|None<br /><br /> EmployeeID|  
|**Boolean**|**boolean**|**boolean**|CONVERT(bit, EmployeeID)|  
|**Десятичной, integer, float, byte, short, int, long, float, double, unsignedByte, типа unsignedShort, unsignedInt, unsignedLong**|**номер, int, float, i1, i2, i4, i8, r4, r8ui1, ui2, ui4, ui8**|**number**|CONVERT(float(53), EmployeeID)|  
|**ID, idref, idrefsentity, сущности, нотации, nmtoken, nmtokens, DateTime, string, AnyURI**|**ID, idref, idrefsentity, сущностей, перечисления, нотации, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid**|**строка**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**decimal**|**fixed14.4**|**Неприменимо (есть тип данных не в XPath, эквивалентного типу fixed14.4 XDR данных.)**|CONVERT(money, EmployeeID)|  
|**date**|**date**|**строка**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**time**|**time**<br /><br /> **Time.TZ**|**строка**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  

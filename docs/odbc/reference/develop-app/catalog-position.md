---
title: Позиция каталога Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0305d978dc4ecd21892a0be3916fa5072b7be95a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303385"
---
# <a name="catalog-position"></a>Положение каталога
Положение имени каталога в идентификаторе и то, как оно отделено от остального идентификатора, варьируется от источника данных к источнику данных. Например, в источнике данных Xbase имя каталога является каталогом, а в Microsoft® Windows®, отделено от имени\\таблицы (которое является именем файла) от backslash ( Следующая иллюстрация демонстрирует это условие.  
  
 ![Положение каталога: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 В исходном коде данных сервера S'L— каталог является базой данных и отделен от схемы и названий таблиц периодом (.).  
  
 ![Положение каталога: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 В источнике данных Oracle каталог также является базой данных, но следует названию таблицы и отделен от схемы и названий таблиц по знаку (кв. м).  
  
 ![Положение каталога: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Чтобы определить сепаратор каталога и местоположение названия каталога, приложение вызывает **S'LGetInfo** с SQL_CATALOG_NAME_SEPARATOR и SQL_CATALOG_LOCATION опций. Совместимые приложения должны создавать идентификаторы в соответствии с этими значениями.  
  
 При цитировании идентификаторов, содержащих более одной части, приложения должны быть осторожны, чтобы процитировать каждую часть отдельно, а не цитировать символ, отделяя идентификаторы. Например, в следующем заявлении, чтобы выбрать все строки и столбцы таблицы Xbase, приводятся имена каталога (XBASE-SALES-CORP), но не\\сепаратор каталога (  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 В следующем заявлении, чтобы выбрать все строки и столбцы таблицы Oracle котировки каталога (Продажи), схема (корпоративные), и таблицы (части) имена, но не каталог (к) или схемы (.) сепараторов:  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Для получения информации о цитировании идентификаторов, см. [Quoted Identifiers](../../../odbc/reference/develop-app/quoted-identifiers.md)

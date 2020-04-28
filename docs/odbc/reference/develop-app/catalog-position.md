---
title: Расположение каталога | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303385"
---
# <a name="catalog-position"></a>Положение каталога
Расположение имени каталога в идентификаторе и его отделение от остальной части идентификатора отличается от источника данных к источнику данных. Например, в источнике данных xbase имя каталога является каталогом, а в Microsoft® Windows® отделяется от имени таблицы (то есть имени файла) на обратную косую черту (\\). Это условие показано на следующем рисунке.  
  
 ![Положение каталога: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 В SQL Server источнике данных каталог является базой данных и отделен от имени схемы и таблицы на точку (.).  
  
 ![Положение каталога: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 В источнике данных Oracle каталог также является базой данных, но соответствует имени таблицы и отделяется от имен схем и таблиц символом @.  
  
 ![Положение каталога: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Чтобы определить разделитель каталога и расположение имени каталога, приложение вызывает **SQLGetInfo** с параметрами SQL_CATALOG_NAME_SEPARATOR и SQL_CATALOG_LOCATION. Приложения, поддерживающие взаимодействие, должны создавать идентификаторы в соответствии с этими значениями.  
  
 При заключении идентификаторов, содержащих более одной части, необходимо заключить в кавычки каждую часть отдельно, а не цитировать символ, разделяющий идентификаторы. Например, следующая инструкция позволяет выбрать все строки и столбцы таблицы xbase в кавычках для имен каталога (\КСБАСЕ\САЛЕС\КОРП) и Table (Parts. dbf), но не для разделителя каталога (\\):  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 Следующая инструкция позволяет выбрать все строки и столбцы таблицы Oracle, в которых заменяются имена каталога (Sales), схемы (организации) и таблицы (частей), но не разделители каталога (@) или схемы (.):  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Сведения об обзнаках идентификаторов см. в следующем разделе [заключенные в кавычки идентификаторы](../../../odbc/reference/develop-app/quoted-identifiers.md).

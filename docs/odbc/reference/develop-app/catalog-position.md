---
title: Положение каталога | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3d7c320521a9948c7968f4f7f5d42fd715f6c03d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062682"
---
# <a name="catalog-position"></a>Положение каталога
Местоположение имени каталога в код и как он отделен от остальной части идентификатора зависит от источника данных к источнику данных. Для этого в источнике данных Xbase имя каталога является каталогом и, в Microsoft® Windows® отделяется от имени таблицы (который является именем файла) обратную косую черту (\\). На следующем рисунке показано это условие.  
  
 ![Положение каталога: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 В источнике данных SQL Server каталог — это база данных и отделяется от имена схемы и таблицы точкой (.).  
  
 ![Положение каталога: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 В источнике данных Oracle, каталог также является базой данных, но следует за именем таблицы и отделяется от их имена схем и таблиц знак (@).  
  
 ![Положение каталога: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Чтобы определить разделитель каталога и местоположение имени каталога, приложение вызывает **SQLGetInfo** параметры SQL_CATALOG_NAME_SEPARATOR и SQL_CATALOG_LOCATION. Взаимодействующие приложения следует создавать идентификаторы в соответствии с этими значениями.  
  
 Когда заключения в кавычки идентификаторов, содержащих более одной части, приложения должны быть осторожность, чтобы цитировать каждая часть отдельно и не Квота символ, разделяющий идентификаторы. Например, следующую инструкцию, чтобы выбрать все строки и столбцы таблицы Xbase квоты каталога (\XBASE\SALES\CORP) и имена таблиц (Parts.dbf), но не разделитель каталога (\\):  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 Следующую инструкцию, чтобы выбрать все строки и столбцы из таблицы Oracle квоты каталога (продажи), схемы (Корпоративная) и имена таблиц (части), но не в каталоге (@) или разделители схемы (.):  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Сведения о заключения в кавычки идентификаторов, см. следующий раздел, [идентификаторы в кавычках](../../../odbc/reference/develop-app/quoted-identifiers.md).

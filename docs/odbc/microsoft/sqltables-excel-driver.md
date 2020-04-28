---
title: SQLTables (драйвер для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c436a1f52a862cda753d8c043515f5584607d98c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299304"
---
# <a name="sqltables-excel-driver"></a>SQLTables (драйвер для Excel)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Excel. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*сзтаблеовнер*|Единственным допустимым аргументом для *сзтаблеовнер* является null, так как ни один из драйверов не поддерживает имена владельцев. Если для *сзтаблеовнер* ЗАДАНО значение null, возвращаются все таблицы. Значение NULL возвращается в столбец TABLE_OWNER.|  
|*сзтаблекуалифиер*|Если используется драйвер Microsoft Excel 3,0 или 4,0, то при вызове **SQLTables** со значением *сзтаблекуалифиер* , которое не является именем существующей таблицы, драйвер создаст таблицу с таким именем.<br /><br /> В столбце TABLE_QUALIFIER **SQLTables** вернет путь к каталогу.|  
|*сзтаблетипе*|Для Microsoft Excel 3,0 или 4,0 "TABLE" — это единственный поддерживаемый тип таблицы.<br /><br /> Для более поздних версий файлов Microsoft Excel «СИСТЕМная таблица» возвращается для имен листов (таблиц с «$» в конце), а «TABLE» — для таблиц на листах.|

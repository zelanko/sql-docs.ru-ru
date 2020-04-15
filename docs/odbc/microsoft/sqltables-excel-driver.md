---
title: СЗЛСтолы (Водитель Excel) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299304"
---
# <a name="sqltables-excel-driver"></a>SQLTables (драйвер для Excel)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах Excel. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*szTableВладелец*|Единственным веским аргументом для *szTableOwner* является NULL, потому что ни один из драйверов не поддерживает имена владельцев. С *набором szTableOwner* null все таблицы возвращаются. NULL возвращается в TABLE_OWNER колонке.|  
|*szTableQualifier*|При использовании драйвера Microsoft Excel 3.0 или 4.0, если вы позвоните в **S'LTables** со значением для *szTablequalifier,* которое не является названием существующей таблицы, драйвер создаст таблицу с этим именем.<br /><br /> В TABLE_QUALIFIER колонке **S'LTables** вернет путь в каталог.|  
|*SzTableType*|Для Microsoft Excel 3.0 или 4.0 "TABLE" является единственным поддерживаемым типом таблицы.<br /><br /> Для более поздних версий файлов Microsoft Excel "SYSTEM TABLE" возвращается для имен листов (таблицы с "$" на конце), а "TABLE" возвращается для таблиц в листах.|

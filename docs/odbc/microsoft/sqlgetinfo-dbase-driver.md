---
title: SQLGetInfo (драйвер для dBASE) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetInfo
ms.assetid: 42ffdc9c-281b-4df5-ac6d-7b34f15ecd4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 603e88703f7a2554ab874a3e5fdd8b4b1a87cda0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833852"
---
# <a name="sqlgetinfo-dbase-driver"></a>SQLGetInfo (драйвер для dBASE)
> [!NOTE]  
>  В этом разделе сведения для dBASE специфические для драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** поддерживает тип SQL_FILE_USAGE сведения. Возвращаемое значение равно 16-разрядное целое число, которое указывает, как драйвер напрямую обрабатывает файлы в источнике данных:  
  
-   SQL_FILE_NOT_SUPPORTED — Драйвер не драйвер среднего уровня.  
  
-   SQL_FILE_TABLE — Драйвер одноуровневых считает файлы в источнике данных таблицы.  
  
-   SQL_FILE_QUALIFIER — Драйвер среднего уровня обрабатывает файлы в источнике данных как квалификатор.  
  
 Поскольку каждый файл представляет собой таблицу, драйвер ODBC возвращает SQL_FILE_TABLE.  
  
## <a name="sqlaltertable"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN &AMP;#124; SQL_AT_DROP_COLUMN  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Версия|Формат номера версий|  
|----------|-------------|-------------------------------|  
|ДЛЯ DBASE|3.0|03.00.0000|  
||4.0|04.00.0000|  
||5.0|05.00.0000|  
  
## <a name="sqlddlindex"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &AMP;#124; SQL_QU_TABLE_DEFINITION &AMP;#124; SQL_QU_INDEX_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_DAYOFMONTH &AMP;#124; SQL_FN_TD_DAYOFWEEK &AMP;#124; SQL_FN_TD_DAYOFYEAR &AMP;#124; SQL_FN_TD_HOUR &AMP;#124; SQL_FN_TD_MINUTE &AMP;#124; SQL_FN_TD_MONTH &AMP;#124; SQL_FN_TD_SECOND &AMP;#124; SQL_FN_TD_WEEK &AMP;#124; SQL_FN_TD_YEAR

---
title: SQLGetInfo (драйвер для Paradox) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Paradox Driver
ms.assetid: 43aab762-68f4-4128-b8f5-8878ea5f1258
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a35f3bdbd68b674736ac22f447a8be45c1342682
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003246"
---
# <a name="sqlgetinfo-paradox-driver"></a>SQLGetInfo (драйвер для Paradox)
> [!NOTE]  
>  Здесь приведены сведения об особенностях драйвер для Paradox. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** поддерживает тип SQL_FILE_USAGE сведения. Возвращаемое значение равно 16-разрядное целое число, которое указывает, как драйвер напрямую обрабатывает файлы в источнике данных:  
  
-   SQL_FILE_NOT_SUPPORTED - драйвер не драйвер среднего уровня.  
  
-   SQL_FILE_TABLE - драйвер одноуровневых считает файлы в источнике данных таблицы.  
  
-   SQL_FILE_QUALIFIER - драйвер среднего уровня обрабатывает файлы в источнике данных как квалификатор.  
  
 Поскольку каждый файл представляет собой таблицу, драйвер ODBC возвращает SQL_FILE_TABLE.  
  
## <a name="sqlaltertable"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN &#124; SQL_AT_DROP_COLUMN  
  
## <a name="sqlddlindex"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Version|Формат номера версий|  
|----------|-------------|-------------------------------|  
|Для Paradox|3.x|03.00.0000|  
||4.x|04.00.0000|  
||5.x|05.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION &#124; SQL_QU_INDEX_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR

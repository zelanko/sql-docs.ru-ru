---
title: SQLGetInfo (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetInfo
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 256e964e556421db62dc8f52fdc6bc759c3a200a
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52536861"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера текстовый файл. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** поддерживает тип SQL_FILE_USAGE сведения. Возвращаемое значение равно 16-разрядное целое число, которое указывает, как драйвер напрямую обрабатывает файлы в источнике данных:  
  
-   SQL_FILE_NOT_SUPPORTED - драйвер не драйвер среднего уровня.  
  
-   SQL_FILE_TABLE - драйвер одноуровневых считает файлы в источнике данных таблицы.  
  
-   SQL_FILE_QUALIFIER - драйвер среднего уровня обрабатывает файлы в источнике данных как квалификатор.  
  
 Поскольку каждый файл представляет собой таблицу, драйвер ODBC для Textdriver возвращает SQL_FILE_TABLE.  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Версия|Формат номера версий|  
|----------|-------------|-------------------------------|  
|Текста|1.0|01.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &AMP;#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &AMP;#124; SQL_FN_TD_CURTIME &AMP;#124; SQL_FN_TD_DAYOFMONTH &AMP;#124; SQL_FN_TD_DAYOFWEEK &AMP;#124; SQL_FN_TD_DAYOFYEAR &AMP;#124; SQL_FN_TD_HOUR &AMP;#124; SQL_FN_TD_MINUTE &AMP;#124; SQL_FN_TD_MONTH &AMP;#124; SQL_FN_TD_NOW &AMP;#124; SQL_FN_TD_SECOND &AMP;#124; SQL_FN_TD_WEEK &AMP;#124; SQL_FN_TD_YEAR

---
title: СЗЛГЕтИнФО (Драйвер текстовых файлов) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09ca2e42e20a6f314de3b68fe5d5b143f41269c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298505"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (драйвер для текстовых файлов)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах, специфийных для драйверов текста. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 **Компания SLGetInfo** поддерживает SQL_FILE_USAGE тип информации. Возвратное значение представляет собой 16-разрядный ряд, который показывает, как драйвер непосредственно относится к файлам в источнике данных:  
  
-   SQL_FILE_NOT_SUPPORTED - Водитель не является одноуровневым водителем.  
  
-   SQL_FILE_TABLE - одноуровневый драйвер рассматривает файлы в источнике данных как таблицы.  
  
-   SQL_FILE_QUALIFIER - одноуровневый драйвер рассматривает файлы в источнике данных как квалификатор.  
  
 Водитель ODBC возвращает SQL_FILE_TABLE для Textdriver, потому что каждый файл представляет собой таблицу.  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|Isam|Version|Формат номеров версий|  
|----------|-------------|-------------------------------|  
|Text|1.0|01.00.0000|  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &#124; SQL_FN_TD_CURTIME &#124; SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_NOW &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR

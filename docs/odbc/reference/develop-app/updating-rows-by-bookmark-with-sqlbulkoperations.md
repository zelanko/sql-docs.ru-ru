---
title: "Обновление строк по закладке с SQLBulkOperations | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], updating rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c626472dd121d39ae01ac90824a7977587401944
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Обновление строк по закладке с SQLBulkOperations
При обновлении строки с закладкой, **SQLBulkOperations** позволяет обновить одну или несколько строк из таблицы источника данных. Строки идентифицируются по закладки в столбце привязанного закладки. Строка обновляется с использованием данных в буферы приложения для каждого привязанного столбца (кроме случаев, когда значение в буфер длины/индикатора для столбца SQL_COLUMN_IGNORE). Несвязанные столбцы не будет обновляться.  
  
 Для обновления строк по закладке с **SQLBulkOperations**, приложение:  
  
1.  Получает и кэширует закладки все обновляемые строки. Если имеется более одного закладки и используется привязка на уровне столбцов, закладки хранятся в массиве; Если имеется более одного закладки и привязка, закладки, хранятся в массив структур строк.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции количество закладок и привязывает буфер, содержащий значение или массив закладки для столбца с номером 0.  
  
3.  Помещает новые значения данных в буферы строк. Сведения о том, как для отправления объемных данных с **SQLBulkOperations**, в разделе [большие объемы данных и SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Задает значение в буфер длины/индикатора каждого столбца при необходимости. Это байтовая длина данных или SQL_NTS для столбцов, привязанных к буферам строк байтовая длина данных для столбцов, привязанных к двоичных буферов и SQL_NULL_DATA для всех столбцов будет присвоено значение NULL.  
  
5.  Задает значение в буфер длины/индикатора этих столбцов, которые не должны быть обновлены для SQL_COLUMN_IGNORE. Несмотря на то, что приложение может пропустить этот шаг и повторно отправить существующих данных, это приведет к неэффективному использованию и риск отправке значений в источнике данных, были усечены при чтении.  
  
6.  Вызовы **SQLBulkOperations** с *операции* SQL_UPDATE_BY_BOOKMARK значение аргумента.  
  
 Для каждой строки, отправляемое в источник данных, как обновление буферы приложения должны иметь допустимую строку данных. Если буферы приложения заполняются выборкой, если была сохранена массив состояния строк, и состояние для строки имеет значение SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW, недопустимые данные может непреднамеренно отправляться к источнику данных.

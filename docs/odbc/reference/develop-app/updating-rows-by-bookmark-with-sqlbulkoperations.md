---
description: Обновление строк по закладкам с помощью SQLBulkOperations
title: Обновление строк по закладке с помощью SQLBulkOperations | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], updating rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9981136d546d53b131cff0d71edcdeab5b2e650c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482877"
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>Обновление строк по закладкам с помощью SQLBulkOperations
При обновлении строки по закладке **SQLBulkOperations** делает источник данных обновлять одну или несколько строк таблицы. Строки определяются закладкой в связанном столбце закладки. Строка обновляется с использованием данных в буферах приложений для каждого привязанного столбца (за исключением случаев, когда значение в буфере длины или индикатора столбца равно SQL_COLUMN_IGNORE). Несвязанные столбцы не будут обновлены.  
  
 Чтобы обновить строки по закладке с помощью **SQLBulkOperations**, приложение:  
  
1.  Извлекает и кэширует закладки всех обновляемых строк. Если используется более одной закладки и привязки на уровне столбца, закладки хранятся в массиве. Если используется более одной закладки и привязки на уровне строк, закладки хранятся в массиве структур строк.  
  
2.  Задает для атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции число закладок и привязывает буфер, содержащий значение закладки, или массив закладок к столбцу 0.  
  
3.  Помещает новые значения данных в буферы набора строк. Сведения о том, как отправить длинные данные с помощью **SQLBulkOperations**, см. в разделе [Long Data and SQLSetPos and SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  При необходимости устанавливает значение в буфере длины и индикатора для каждого столбца. Это длина байта данных или SQL_NTS для столбцов, привязанных к буферам строк, длина байтов данных для столбцов, привязанных к двоичным буферам, и SQL_NULL_DATA для всех столбцов, для которых задано значение NULL.  
  
5.  Задает значение в буфере длины или индикатора для столбцов, которые не обновляются до SQL_COLUMN_IGNORE. Несмотря на то, что приложение может пропустить этот шаг и повторно отправить существующие данные, это неэффективно и риски отправляют значения в источник данных, который был усечен при чтении.  
  
6.  Вызывает **SQLBulkOperations** с аргументом *операции* , для которого задано значение SQL_UPDATE_BY_BOOKMARK.  
  
 Для каждой строки, которая отправляется в источник данных как обновление, буферы приложения должны иметь допустимые данные строк. Если буферы приложений были заполнены путем выборки, если массив состояния строк был сохранен, а значение состояния для строки — SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW, недопустимые данные могут быть непреднамеренно отправлены в источник данных.

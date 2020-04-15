---
title: Удалять строки по закладке с помощью S'LBulkOperations (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b6a4c1b24ee276c86175392eb45ac5ce0aa45e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305965"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Удаление строк по закладкам с помощью SQLBulkOperations
При удалении строки по закладке, **S'LBulkOperations** заставляет источник данных удалять один или несколько выбранных строк таблицы. Строки идентифицируются закладкой в связанной колонке закладок.  
  
 Для удаления строк по закладке с **помощью S'LBulkOperations**приложение выполняет следующее:  
  
1.  Извлекает и кэширует закладки всех строк, которые должны быть удалены. При использовании более одной закладки и привязки к столбцом закладки закладки хранятся в массиве; если используется несколько закладок и используется связывание с рядом, закладки хранятся в массиве структур строки.  
  
2.  Устанавливает SQL_ATTR_ROW_ARRAY_SIZE заявление атрибутом к числу закладок и связывает буфер, содержащий значение закладки, или массив закладок, к столбу 0.  
  
3.  Вызывает **S'LBulkOperations** с *операцией,* установленной для SQL_DELETE_BY_BOOKMARK.

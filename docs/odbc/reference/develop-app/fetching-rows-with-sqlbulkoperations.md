---
title: Получение строк с помощью S'LBulkOperations (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae0b4c2114059cecaaf8f8825169300f131bd473
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305653"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Выборка строк с помощью SQLBulkOperations
Данные могут быть повторно извлечены в ряд, используя закладки, позвонив в **S'LBulkOperations.** Строки, которые должны быть извлечены, идентифицируются закладками в связанной колонке закладок. Колонны со значением SQL_COLUMN_IGNORE не извлекаются.  
  
 Для выполнения оптовых извлечений с **помощью S'LBulkOperations**, приложение делает следующее:  
  
1.  Извлекает и кэширует закладки всех строк, которые будут обновлены. При использовании более одной закладки и привязки к столбцом закладки закладки хранятся в массиве; если используется несколько закладок и используется связывание с рядом, закладки хранятся в массиве структур строки.  
  
2.  Устанавливает SQL_ATTR_ROW_ARRAY_SIZE значение оператора к числу строк для получения и связывает буфер, содержащий значение закладки, или массив закладок, к столбу 0.  
  
3.  Устанавливает значение в буфере длины/индикатора каждого столбца по мере необходимости. Это длина данных или SQL_NTS для столбцов, привязанных к строке буферов, длина байт данных для столбцов, привязанных к бинарным буферам, и SQL_NULL_DATA для любых столбцов, которые будут установлены на NULL. Приложение устанавливает значение в буфере длины/индикатора тех столбцов, которые должны быть установлены по умолчанию (если он существует) или NULL (если нет) для SQL_COLUMN_IGNORE.  
  
4.  Вызывает **S'LBulkOperations** с аргументом *операции,* установленным для SQL_FETCH_BY_BOOKMARK.  
  
 Нет необходимости в использовании массива операции строки для предотвращения выполнения операции на определенных столбцах. Приложение выбирает строки, которые оно хочет получить, копируя только закладки для этих строк в связанный массив закладок.

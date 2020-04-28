---
title: Выборка строк с помощью SQLBulkOperations | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305653"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Выборка строк с помощью SQLBulkOperations
Данные можно повторно извлечь в набор строк с помощью закладок путем вызова **SQLBulkOperations.** Извлекаемые строки идентифицируются по закладкам в связанном столбце закладки. Столбцы со значением SQL_COLUMN_IGNORE не извлекаться.  
  
 Для выполнения групповой выборки с помощью **SQLBulkOperations**приложение выполняет следующие действия:  
  
1.  Извлекает и кэширует закладки всех обновляемых строк. Если используется более одной закладки и привязки на уровне столбца, закладки хранятся в массиве. Если используется более одной закладки и привязки на уровне строк, закладки хранятся в массиве структур строк.  
  
2.  Устанавливает атрибут инструкции SQL_ATTR_ROW_ARRAY_SIZE в число извлекаемых строк и привязывает буфер, содержащий значение закладки, или массив закладок к столбцу 0.  
  
3.  При необходимости устанавливает значение в буфере длины и индикатора для каждого столбца. Это длина байта данных или SQL_NTS для столбцов, привязанных к буферам строк, длина байтов данных для столбцов, привязанных к двоичным буферам, и SQL_NULL_DATA для всех столбцов, для которых задано значение NULL. Приложение задает значение в буфере длины или индикатора для столбцов, которые должны быть установлены в значения по умолчанию (если они существуют), или значение NULL (если оно не определено) для SQL_COLUMN_IGNORE.  
  
4.  Вызывает **SQLBulkOperations** с аргументом *операции* , для которого задано значение SQL_FETCH_BY_BOOKMARK.  
  
 Приложению не нужно использовать массив операций строк для предотвращения выполнения операции над определенными столбцами. Приложение выбирает строки, которые требуется получить, копируя только закладки для этих строк в привязанный массив закладок.

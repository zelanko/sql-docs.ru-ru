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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a99592210ff315db026d60b8743d4a3bca13c969
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791542"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Выборка строк с помощью SQLBulkOperations
Данные можно refetched в набор строк с помощью закладок с помощью вызова **SQLBulkOperations.** Строки, которые необходимо извлечь идентифицируются по закладки столбца привязанного закладки. Столбцы со значением SQL_COLUMN_IGNORE не извлекаются.  
  
 Для выполнения операций массовой выборки с **SQLBulkOperations**, приложение выполняет следующие:  
  
1.  Получает и кэширует закладки все обновляемые строки. Если имеется более одного закладки и используется привязка на уровне столбцов, закладки, хранятся в массиве. Если имеется более одного закладки и используется привязка на уровне строки, закладки, хранятся в массив структур строк.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции количество строк для выборки и привязывает буфер, содержащий значение, или массив, закладок, столбец 0.  
  
3.  Задает значение в буфер длины/индикатора каждого столбца, при необходимости. Это байтовая длина данных или SQL_NTS для столбцов, привязанных к буферам строк байтовая длина данных для столбцов, привязанных к двоичных буферах и SQL_NULL_DATA для всех столбцов будет присвоено значение NULL. Приложение задает значение в буфер длины/индикатора тех столбцов, которые требуется задать по умолчанию (если он существует) или значение NULL (если нет) SQL_COLUMN_IGNORE.  
  
4.  Вызовы **SQLBulkOperations** с *операции* аргумент значение SQL_FETCH_BY_BOOKMARK.  
  
 Нет необходимости для приложения с помощью массива операций строк предотвращается выполняемых на определенные столбцы. Приложение выбирает строки, которые он хочет получить путем копирования закладки только для тех строк, в массиве привязанных закладки.

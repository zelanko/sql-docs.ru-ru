---
title: "Выборка строк с SQLBulkOperations | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b3af3d83d9d0dab4735842621bbcb49fab69a4c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Выборка строк с SQLBulkOperations
Данные можно refetched в набор строк с помощью закладок с помощью вызова **SQLBulkOperations.** Строки, которые должны быть извлечены идентифицируются по закладки в столбце привязанного закладки. Не выбраны столбцы со значением SQL_COLUMN_IGNORE.  
  
 Для выполнения массового выборки с **SQLBulkOperations**, приложение делает следующее:  
  
1.  Получает и кэширует закладки все обновляемые строки. Если имеется более одного закладки и используется привязка на уровне столбцов, закладки хранятся в массиве; Если имеется более одного закладки и привязка, закладки, хранятся в массив структур строк.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции количество строк для выборки и привязывает буфер, содержащий значение или массив закладки для столбца с номером 0.  
  
3.  Задает значение в буфер длины/индикатора каждого столбца при необходимости. Это байтовая длина данных или SQL_NTS для столбцов, привязанных к буферам строк байтовая длина данных для столбцов, привязанных к двоичных буферов и SQL_NULL_DATA для всех столбцов будет присвоено значение NULL. Приложение задает значение в буфер длины/индикатора те столбцы, которые должны быть заданы по умолчанию (если он существует) или значение NULL (если нет) SQL_COLUMN_IGNORE.  
  
4.  Вызовы **SQLBulkOperations** с *операции* SQL_FETCH_BY_BOOKMARK значение аргумента.  
  
 Нет необходимости для приложения с помощью массива операций строк Запретить операцию для выполнения на определенные столбцы. Приложение выбирает строки, которые необходимо извлечь, скопировав закладки только для тех строк, в массиве привязанных закладки.

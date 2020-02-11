---
title: Функции каталога | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 232d2e9b7e9eb695a40058075ea511392e464a32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064403"
---
# <a name="catalog-functions"></a>Функции работы с каталогами
Все базы данных имеют структуру, которая описывает, как данные будут храниться в базе данных. Например, простая база данных заказов на продажу может иметь структуру, показанную на следующем рисунке, в которой столбцы ИДЕНТИФИКАТОРов используются для связи таблиц.  
  
 ![Структура простой базы данных](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Эта структура вместе с другими сведениями, такими как привилегии, хранится в наборе системных таблиц, называемых *каталогом* базы данных, который также называется *словарем данных*.  
  
 Приложение может обнаружить эту структуру с помощью вызовов *функций каталога*. Функции каталога возвращают сведения в результирующих наборах и обычно реализуются с помощью инструкций **SELECT** для таблиц в каталоге. Например, приложение может запросить результирующий набор, содержащий сведения о всех таблицах в системе или всех столбцах в определенной таблице.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Функции работы с каталогами в ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)

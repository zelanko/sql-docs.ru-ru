---
description: Функции работы с каталогами
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b75e6a40252f06f6b9e2105bd557fd35ded9243f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465946"
---
# <a name="catalog-functions"></a>Функции работы с каталогами
Все базы данных имеют структуру, которая описывает, как данные будут храниться в базе данных. Например, простая база данных заказов на продажу может иметь структуру, показанную на следующем рисунке, в которой столбцы ИДЕНТИФИКАТОРов используются для связи таблиц.  
  
 ![Структура простой базы данных](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Эта структура вместе с другими сведениями, такими как привилегии, хранится в наборе системных таблиц, называемых *каталогом* базы данных, который также называется *словарем данных*.  
  
 Приложение может обнаружить эту структуру с помощью вызовов *функций каталога*. Функции каталога возвращают сведения в результирующих наборах и обычно реализуются с помощью инструкций **SELECT** для таблиц в каталоге. Например, приложение может запросить результирующий набор, содержащий сведения о всех таблицах в системе или всех столбцах в определенной таблице.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Функции работы с каталогами в ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)

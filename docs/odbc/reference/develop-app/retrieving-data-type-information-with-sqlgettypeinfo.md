---
description: Получение сведений о типе данных с помощью SQLGetTypeInfo
title: Получение сведений о типах данных с помощью SQLGetTypeInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7135a6d149646c43eb93218d2ce8952930748c6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476526"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Получение сведений о типе данных с помощью SQLGetTypeInfo
Поскольку сопоставления между базовыми типами данных SQL и идентификаторами типов ODBC являются приблизительными, ODBC предоставляет функцию (**SQLGetTypeInfo**), с помощью которой драйвер может полностью описать каждый тип данных SQL в источнике данных. Эта функция возвращает результирующий набор, каждая строка которого описывает характеристики одного типа данных, такие как имя, идентификатор типа, точность, масштаб и допустимость значений NULL.  
  
 Эти сведения обычно используются универсальными приложениями, которые позволяют пользователю создавать и изменять таблицы. Такие приложения вызывают **SQLGetTypeInfo** для получения сведений о типе данных, а затем представляют их некоторым или всем пользователям. Такие приложения должны быть осведомлены о двух вещах:  
  
-   Несколько типов данных SQL могут сопоставляться с одним идентификатором типа, что может усложнить определение используемого типа данных. Для решения этой проблемы результирующий набор упорядочивается сначала по идентификатору типа, а второй — по близкости к определению идентификатора типа. Кроме того, типы данных, определяемые источником данных, имеют приоритет над определяемыми пользователем типами данных. Например, предположим, что источник данных определяет типы данных INTEGER и COUNTER одинаково, за исключением того, что счетчик автоматически увеличивается. Предположим также, что определяемый пользователем тип ВХОЛЕНУМ является синонимом ЦЕЛОго числа. Каждый из этих типов сопоставляется с SQL_INTEGER. В результирующем наборе **SQLGetTypeInfo** сначала отображается целое число, а затем — вхоленум, а затем Counter. ВХОЛЕНУМ отображается после ЦЕЛОго числа, поскольку он определен пользователем, но до СЧЕТЧИКа, так как он более точно соответствует определению идентификатора типа SQL_INTEGER.  
  
-   ODBC не определяет имена типов данных для использования в инструкциях **CREATE TABLE** и **ALTER TABLE** . Вместо этого приложение должно использовать имя, возвращенное в столбце TYPE_NAME результирующего набора, возвращаемого функцией **SQLGetTypeInfo**. Это связано с тем, что хотя большая часть SQL не сильно различается в СУБД, имена типов данных отличаются невероятно. Вместо того чтобы принудительно использовать драйверы для анализа инструкций SQL и замены стандартных имен типов данных на имена типов данных СУБД, ODBC требует, чтобы приложения использовали специфические имена СУБД в первую очередь.  
  
 Обратите внимание, что **SQLGetTypeInfo** не обязательно описывает все типы данных, которые могут встретиться в приложении. В частности, результирующие наборы могут содержать типы данных, не поддерживаемые непосредственно источником данных. Например, типы данных столбцов в результирующих наборах, возвращаемых функциями каталога, определяются ODBC, и эти типы данных могут не поддерживаться источником данных. Чтобы определить характеристики типов данных в результирующем наборе, приложение вызывает **SQLColAttribute**.

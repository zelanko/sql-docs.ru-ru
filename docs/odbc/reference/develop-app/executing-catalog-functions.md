---
title: Выполнение функций каталога | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc53e265ffa25c5ec598187f62505f18436f1c69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248336"
---
# <a name="executing-catalog-functions"></a>Выполнение функций каталога
Функции каталога создает результирующий набор, она эквивалентна выполнение любой инструкции SQL результат формирования набора. На самом деле функции работы с каталогами часто реализуются путем вызова стандартных инструкций SQL или вызов стандартных процедур, которые входят в состав драйвера или СУБД. Практически все, что применяется в инструкции SQL, которые создают результирующие наборы также применяется к функции работы с каталогами. Например, атрибут инструкции SQL_ATTR_MAX_ROWS ограничивает число строк, возвращаемых с помощью функции каталога, так же, как он ограничивает число строк, возвращенных **ВЫБЕРИТЕ** инструкции.  
  
 Чтобы выполнить функцию каталога, приложение просто вызывает функцию.  
  
 Дополнительные сведения о функции работы с каталогами, см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).

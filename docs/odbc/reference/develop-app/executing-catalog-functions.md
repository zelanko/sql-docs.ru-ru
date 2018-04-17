---
title: Выполнение функции каталога | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9c50bbb813c0aad7ae8d9a531458b2999dcae86f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="executing-catalog-functions"></a>Выполнение функций каталога
Функции каталога создает результирующий набор, он эквивалентен выполнение любой инструкции SQL результирующий набор генерации. На самом деле функции работы с каталогами часто реализуются путем вызова стандартных инструкций SQL или вызов стандартных процедур, поставляемых вместе с драйвером или СУБД. Практически все, что применяется для инструкций SQL, создающих результирующие наборы также применяется к функции работы с каталогами. Например, атрибут инструкции SQL_ATTR_MAX_ROWS ограничивает число строк, возвращаемых функцией каталога, так же, как она ограничивает число строк, возвращенных **ВЫБЕРИТЕ** инструкции.  
  
 Чтобы выполнить функцию каталога, приложение вызывает функцию.  
  
 Дополнительные сведения о функции каталогов см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).

---
title: "Выполнение функции каталога | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 489cd057a15e90794c71cfb433931cd9bc687016
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="executing-catalog-functions"></a>Выполнение функций каталога
Функции каталога создает результирующий набор, он эквивалентен выполнение любой инструкции SQL результирующий набор генерации. На самом деле функции работы с каталогами часто реализуются путем вызова стандартных инструкций SQL или вызов стандартных процедур, поставляемых вместе с драйвером или СУБД. Практически все, что применяется для инструкций SQL, создающих результирующие наборы также применяется к функции работы с каталогами. Например, атрибут инструкции SQL_ATTR_MAX_ROWS ограничивает число строк, возвращаемых функцией каталога, так же, как она ограничивает число строк, возвращенных **ВЫБЕРИТЕ** инструкции.  
  
 Чтобы выполнить функцию каталога, приложение вызывает функцию.  
  
 Дополнительные сведения о функции каталогов см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).

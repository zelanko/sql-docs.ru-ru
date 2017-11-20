---
title: "Регистр идентификатора | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c55118fa47337425e715a8b3d6409525668e383f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="identifier-case"></a>Регистр идентификатора
В инструкциях SQL и аргументы функций каталога, идентификаторы и заключенные в кавычки идентификаторы может быть либо с учетом регистра или не так, что приложение может определить, вызвав **SQLGetInfo** SQL_IDENTIFIER_CASE и SQL_QUOTED_ Параметры IDENTIFIER_CASE.  
  
 Каждый из этих параметров имеет четыре возможные возвращаемые значения: один о том, идентификатор или заключенный в кавычки идентификатор случай конфиденциальные и три о том, что он не конфиденциальные. Три значения, которые не учитывают регистр расширенного описания случай, в котором хранятся идентификаторы в системном каталоге. Как идентификаторы хранятся в системном каталоге действителен только для отображения, например, если приложение отображает результаты функции каталога; Это не приводит к изменению учет регистра в идентификаторах.


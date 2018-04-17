---
title: Регистр идентификатора | Документы Microsoft
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
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 122f4dfdfab25f246858b36f7753413d25f2eea4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="identifier-case"></a>Регистр идентификатора
В инструкциях SQL и аргументы функций каталога, идентификаторы и заключенные в кавычки идентификаторы может быть либо с учетом регистра или не так, что приложение может определить, вызвав **SQLGetInfo** SQL_IDENTIFIER_CASE и SQL_QUOTED_ Параметры IDENTIFIER_CASE.  
  
 Каждый из этих параметров имеет четыре возможные возвращаемые значения: один о том, идентификатор или заключенный в кавычки идентификатор случай конфиденциальные и три о том, что он не конфиденциальные. Три значения, которые не учитывают регистр расширенного описания случай, в котором хранятся идентификаторы в системном каталоге. Как идентификаторы хранятся в системном каталоге действителен только для отображения, например, если приложение отображает результаты функции каталога; Это не приводит к изменению учет регистра в идентификаторах.

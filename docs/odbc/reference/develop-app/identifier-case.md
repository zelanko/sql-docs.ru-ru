---
title: Регистр идентификатора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66218fb955a4133a5c689f72ab8f4b96504c9bd2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908857"
---
# <a name="identifier-case"></a>Регистр идентификатора
В инструкциях SQL и аргументы функций каталога, идентификаторы и заключенные в кавычки идентификаторы может быть либо с учетом регистра или не так, что приложение может определить, вызвав **SQLGetInfo** SQL_IDENTIFIER_CASE и SQL_QUOTED_ Параметры IDENTIFIER_CASE.  
  
 Каждый из этих параметров имеет четыре возможные возвращаемые значения: один о том, идентификатор или заключенный в кавычки идентификатор случай конфиденциальные и три о том, что он не конфиденциальные. Три значения, которые не учитывают регистр расширенного описания случай, в котором хранятся идентификаторы в системном каталоге. Как идентификаторы хранятся в системном каталоге действителен только для отображения, например, если приложение отображает результаты функции каталога; Это не приводит к изменению учет регистра в идентификаторах.

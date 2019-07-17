---
title: Регистр идентификатора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70728908f081ab89e08cad1265f04394f29b66ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138966"
---
# <a name="identifier-case"></a>Регистр идентификатора
В инструкциях SQL и аргументы функции каталога, идентификаторы и заключенные в кавычки идентификаторы может быть либо с учетом регистра или не так, что приложение может определить, вызвав **SQLGetInfo** SQL_IDENTIFIER_CASE и SQL_QUOTED_ Параметры IDENTIFIER_CASE.  
  
 Каждый из этих вариантов имеет четыре возможные возвращаемые значения: одно сообщение о том, что идентификатор или заключенный в кавычки идентификатор случай конфиденциальные и три о том, что не конфиденциальные. Три значения, которые не учитывают регистр более подробно описывают случай, в котором идентификаторы хранятся в системном каталоге. Каким образом идентификаторы хранятся в системном каталоге действителен только для отображения, например, если приложение отображает результаты функции каталога; учет регистра в идентификаторах не затрагивает.

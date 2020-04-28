---
title: Регистр идентификаторов | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940d96ece6b2c344fa02e0daadd6248270f4d19e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300154"
---
# <a name="identifier-case"></a>Регистр идентификатора
В инструкциях SQL и аргументах функции каталога идентификаторы и идентификаторы в кавычках могут быть либо чувствительны к регистру, либо нет, что может быть определено приложением путем вызова **SQLGetInfo** с параметрами SQL_IDENTIFIER_CASE и SQL_QUOTED_IDENTIFIER_CASE.  
  
 Каждый из этих параметров имеет четыре возможных возвращаемых значения: один из них, указывающий, что идентификатор или идентификатор в кавычках является конфиденциальным, а три сообщает, что он не является конфиденциальным. Три значения без учета регистра описывают случай, в котором идентификаторы хранятся в системном каталоге. Хранение идентификаторов в системном каталоге уместно только для целей отображения, например, когда приложение отображает результаты функции каталога. Он не меняет чувствительность к регистру идентификаторов.

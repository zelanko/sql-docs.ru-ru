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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70728908f081ab89e08cad1265f04394f29b66ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138966"
---
# <a name="identifier-case"></a>Регистр идентификатора
В инструкциях SQL и аргументах функции каталога идентификаторы и идентификаторы в кавычках могут быть либо чувствительны к регистру, либо нет, что может быть определено приложением путем вызова **SQLGetInfo** с параметрами SQL_IDENTIFIER_CASE и SQL_QUOTED_IDENTIFIER_CASE.  
  
 Каждый из этих параметров имеет четыре возможных возвращаемых значения: один из них, указывающий, что идентификатор или идентификатор в кавычках является конфиденциальным, а три сообщает, что он не является конфиденциальным. Три значения без учета регистра описывают случай, в котором идентификаторы хранятся в системном каталоге. Хранение идентификаторов в системном каталоге уместно только для целей отображения, например, когда приложение отображает результаты функции каталога. Он не меняет чувствительность к регистру идентификаторов.

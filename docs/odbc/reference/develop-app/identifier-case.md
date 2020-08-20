---
description: Регистр идентификатора
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
ms.openlocfilehash: ccac9b10e6a32c7265cd5f591944735454b85f80
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461446"
---
# <a name="identifier-case"></a>Регистр идентификатора
В инструкциях SQL и аргументах функции каталога идентификаторы и идентификаторы в кавычках могут быть либо чувствительны к регистру, либо нет, что может быть определено приложением путем вызова **SQLGetInfo** с параметрами SQL_IDENTIFIER_CASE и SQL_QUOTED_IDENTIFIER_CASE.  
  
 Каждый из этих параметров имеет четыре возможных возвращаемых значения: один из них, указывающий, что идентификатор или идентификатор в кавычках является конфиденциальным, а три сообщает, что он не является конфиденциальным. Три значения без учета регистра описывают случай, в котором идентификаторы хранятся в системном каталоге. Хранение идентификаторов в системном каталоге уместно только для целей отображения, например, когда приложение отображает результаты функции каталога. Он не меняет чувствительность к регистру идентификаторов.

---
title: Идентификатор Дело Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300154"
---
# <a name="identifier-case"></a>Регистр идентификатора
В заявлениях и аргументах функции каталога, идентификаторах и идентификаторах функции каталога могут быть либо чувствительными к случаям, либо нет, что приложение может определить, позвонив в **S'LGetInfo** с SQL_IDENTIFIER_CASE и SQL_QUOTED_IDENTIFIER_CASE вариантами.  
  
 Каждый из этих вариантов имеет четыре возможных значения возврата: один из них указывает на то, что случай идентификатора или приведенный идентификатор является чувствительным, а три — о том, что он не является чувствительным. Три значения, не чувствительные к случаям, далее описывают случай, в котором идентификаторы хранятся в каталоге системы. Способ хранения идентификаторов в каталоге системы актуален только для целей отображения, например, когда приложение отображает результаты функции каталога; это не меняет чувствительность к случаям идентификаторов.

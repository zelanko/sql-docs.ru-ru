---
title: Зарезервированные слова ограничения | Документы Microsoft
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac61a7aa818ef3593fddc630d5027fbf7e4aa211
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="reserved-keyword-limitations"></a>Ограничения зарезервированное ключевое слово

Избегайте использования ODBC зарезервированные ключевые слова в качестве идентификаторов в таблицы SQL или связанные объекты. Если возникает так, где необходимо использовать в качестве идентификатора зарезервированное ключевое слово, идентификатор необходимо заключить в пару *backticks* ('). Другое имя для *обратный апостроф* — *Обратная кавычка*.

Зарезервированное ключевое слово ограничение также применяется к любой сокращенный зарезервированных ключевых слов.

Список зарезервированных ключевых слов ODBC можно найти в:

- [Зарезервированные ключевые слова ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- В *руководство по программированию ODBC*, в разделе [грамматику SQL приложение C:](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).


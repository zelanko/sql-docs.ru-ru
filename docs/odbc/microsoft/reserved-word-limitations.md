---
title: Зарезервированные ограничения формата Word | Документация Майкрософт
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 531a100fed389264d9af6a1733636792a3dc7920
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764492"
---
# <a name="reserved-keyword-limitations"></a>Ограничения зарезервированное ключевое слово

Старайтесь не использовать любой зарезервированных ключевых слов ODBC в таблицы SQL или связанные объекты в качестве идентификаторов. Если нечетное случай возникает, когда необходимо использовать как идентификатор является зарезервированным ключевым словом, они должны быть заключены идентификатор с парой *обратных апострофа* ('). Другое имя для *обратный апостроф* — *Обратная кавычка*.

Зарезервированное ключевое слово ограничение также применяется к любой краткая форма зарезервированные ключевые слова.

Список зарезервированных ключевых слов ODBC можно найти по адресу:

- [Зарезервированные ключевые слова ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- В *справочное руководство по программированию ODBC*, см. в разделе [грамматике SQL в C: приложение](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).


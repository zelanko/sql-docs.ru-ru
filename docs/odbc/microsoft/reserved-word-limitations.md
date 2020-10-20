---
description: Ограничения зарезервированных ключевых слов
title: Ограничения зарезервированных слов | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15033816b953df764126853ada353452f00650d6
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196178"
---
# <a name="reserved-keyword-limitations"></a>Ограничения зарезервированных ключевых слов

Не используйте зарезервированные ключевые слова ODBC в качестве идентификаторов в таблицах SQL или связанных объектах. Если возникает случай, когда в качестве идентификатора необходимо использовать зарезервированное ключевое слово, необходимо заключить идентификатор в пару обратных *импульсов* ('). Другое *имя для* *обратной стороны — Обратная кавычка*.

Зарезервированное ограничение ключевого слова также применяется к любой сокращенной форме зарезервированных ключевых слов.

Список зарезервированных ключевых слов ODBC можно найти по адресу:

- [Зарезервированные ключевые слова ODBC](../reference/appendixes/reserved-keywords.md).

- В *справочном руководстве программиста по ODBC*см. [Приложение C: грамматика SQL](../reference/appendixes/appendix-c-sql-grammar.md).
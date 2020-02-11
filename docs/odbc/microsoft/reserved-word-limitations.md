---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c884d8594c3c4511bed0e24f9b3dd43092176b4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67988025"
---
# <a name="reserved-keyword-limitations"></a>Ограничения зарезервированных ключевых слов

Не используйте зарезервированные ключевые слова ODBC в качестве идентификаторов в таблицах SQL или связанных объектах. Если возникает случай, когда в качестве идентификатора необходимо использовать зарезервированное ключевое слово, необходимо заключить идентификатор в пару обратных *импульсов* ('). Другое *имя для* *обратной стороны — Обратная кавычка*.

Зарезервированное ограничение ключевого слова также применяется к любой сокращенной форме зарезервированных ключевых слов.

Список зарезервированных ключевых слов ODBC можно найти по адресу:

- [Зарезервированные ключевые слова ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- В *справочном руководстве программиста по ODBC*см. [Приложение C: грамматика SQL](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).


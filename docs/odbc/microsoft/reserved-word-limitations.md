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
ms.openlocfilehash: 07917cbe056b38be42e4697fcef52935bae3efe3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449296"
---
# <a name="reserved-keyword-limitations"></a>Ограничения зарезервированных ключевых слов

Не используйте зарезервированные ключевые слова ODBC в качестве идентификаторов в таблицах SQL или связанных объектах. Если возникает случай, когда в качестве идентификатора необходимо использовать зарезервированное ключевое слово, необходимо заключить идентификатор в пару обратных *импульсов* ('). Другое *имя для* *обратной стороны — Обратная кавычка*.

Зарезервированное ограничение ключевого слова также применяется к любой сокращенной форме зарезервированных ключевых слов.

Список зарезервированных ключевых слов ODBC можно найти по адресу:

- [Зарезервированные ключевые слова ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- В *справочном руководстве программиста по ODBC*см. [Приложение C: грамматика SQL](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).


---
title: Список зарезервированных слов Jet 4.0 использует SQL-92 при ExtendedAnsiSQL_Set | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
- extendedANSISQL [ODBC], reserved words
ms.assetid: 7645187e-7777-4c07-9686-0a80d5c5834d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7eb68eb67e1bac0441a9130824d6f79e1497076
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisqlset"></a>Список зарезервированных слов Jet 4.0 использует SQL-92 при ExtendedAnsiSQL_Set
При включении флаг ExtendedAnsiSQL Jet 4.0 использует список зарезервированных слов SQL-92. Попытка использовать SQL-92 зарезервированным словом, как имя объекта, не заключенные в кавычки приведет к синтаксической ошибки. При отключении флаг ExtendedAnsiSQL новые зарезервированные слова можно использовать как имена объектов в виде до.

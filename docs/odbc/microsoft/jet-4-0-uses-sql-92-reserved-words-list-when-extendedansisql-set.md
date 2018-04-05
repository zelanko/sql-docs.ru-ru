---
title: Список зарезервированных слов Jet 4.0 использует SQL-92 при ExtendedAnsiSQL_Set | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extendedANSISQL [ODBC], reserved words
ms.assetid: 7645187e-7777-4c07-9686-0a80d5c5834d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8fb1b9b7aec3b0456dc65dd1294403d2b934a4a3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisqlset"></a>Список зарезервированных слов Jet 4.0 использует SQL-92 при ExtendedAnsiSQL_Set
При включении флаг ExtendedAnsiSQL Jet 4.0 использует список зарезервированных слов SQL-92. Попытка использовать SQL-92 зарезервированным словом, как имя объекта, не заключенные в кавычки приведет к синтаксической ошибки. При отключении флаг ExtendedAnsiSQL новые зарезервированные слова можно использовать как имена объектов в виде до.

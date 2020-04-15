---
title: Jet 4.0 использует список зарезервированных слов S'L-92, когда ExtendedAnsiSQL_Set Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], reserved words
ms.assetid: 7645187e-7777-4c07-9686-0a80d5c5834d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6988e0da1ecb881e0f6e88e35b66f1a6284f9b7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299964"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 использует список зарезервированных слов SQL-92 для ExtendedAnsiSQL_Set
При включении флага ExtendedAnsiS'L Jet 4.0 используется список зарезервированных слов S'L-92. Попытка использовать зарезервированное слово S'L-92 в качестве нецитируемого имени объекта приведет к ошибке синтаксиса. При выключении флага ExtendedAnsiS'L новые зарезервированные слова могут использоваться в качестве имен объектов, как и раньше.

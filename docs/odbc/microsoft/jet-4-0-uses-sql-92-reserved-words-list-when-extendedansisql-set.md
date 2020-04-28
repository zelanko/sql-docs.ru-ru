---
title: В Jet 4,0 используется список зарезервированных слов SQL-92 при ExtendedAnsiSQL_Set | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299964"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 использует список зарезервированных слов SQL-92 для ExtendedAnsiSQL_Set
Если флаг ExtendedAnsiSQL включен, Jet 4,0 использует зарезервированные слова SQL-92. Попытка использовать зарезервированное слово SQL-92 в качестве имени объекта, не заключенного в кавычки, приведет к синтаксической ошибке. Если флаг ExtendedAnsiSQL выключен, новые зарезервированные слова можно использовать в качестве имен объектов.

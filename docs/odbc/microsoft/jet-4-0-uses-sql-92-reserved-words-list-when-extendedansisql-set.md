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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93d23216db950ed861449061f3e35e5e88a637fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68058787"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 использует список зарезервированных слов SQL-92 для ExtendedAnsiSQL_Set
Если флаг ExtendedAnsiSQL включен, Jet 4,0 использует зарезервированные слова SQL-92. Попытка использовать зарезервированное слово SQL-92 в качестве имени объекта, не заключенного в кавычки, приведет к синтаксической ошибке. Если флаг ExtendedAnsiSQL выключен, новые зарезервированные слова можно использовать в качестве имен объектов.

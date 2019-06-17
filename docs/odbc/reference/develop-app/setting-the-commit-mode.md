---
title: Настройка режима фиксации | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efc999a3644a9146e7195f0bbbb07d130172d30d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62445936"
---
# <a name="setting-the-commit-mode"></a>Настройка режима фиксации
Приложения указать режим транзакции с помощью атрибута соединения SQL_ATTR_AUTOCOMMIT. По умолчанию ODBC транзакции находятся в режиме автоматической фиксации (если только не **SQLSetConnectAttr** и **SQLSetConnectOption** не поддерживаются, наверняка). Переключение из режима ручной фиксации на режим автоматической фиксации автоматически фиксирует любой открытой транзакции в соединении.

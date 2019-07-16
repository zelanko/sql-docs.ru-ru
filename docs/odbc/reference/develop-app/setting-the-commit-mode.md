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
ms.openlocfilehash: a43a78ad9453f65d9b12595851bd622f720b409a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094222"
---
# <a name="setting-the-commit-mode"></a>Настройка режима фиксации
Приложения указать режим транзакции с помощью атрибута соединения SQL_ATTR_AUTOCOMMIT. По умолчанию ODBC транзакции находятся в режиме автоматической фиксации (если только не **SQLSetConnectAttr** и **SQLSetConnectOption** не поддерживаются, наверняка). Переключение из режима ручной фиксации на режим автоматической фиксации автоматически фиксирует любой открытой транзакции в соединении.

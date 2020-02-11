---
title: Установка режима фиксации | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094222"
---
# <a name="setting-the-commit-mode"></a>Настройка режима фиксации
Приложения указывают режим транзакций с атрибутом подключения SQL_ATTR_AUTOCOMMIT. По умолчанию транзакции ODBC находятся в режиме автоматической фиксации (если не поддерживаются **SQLSetConnectAttr** и **SQLSetConnectOption** , что маловероятно). Переключение из режима ручной фиксации в режим автоматической фиксации автоматически фиксирует все открытые транзакции в соединении.

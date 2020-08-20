---
description: Настройка режима фиксации
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a71d6f97f4683f9177c940be7d6ca1cc4a27c01
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494628"
---
# <a name="setting-the-commit-mode"></a>Настройка режима фиксации
Приложения указывают режим транзакций с атрибутом подключения SQL_ATTR_AUTOCOMMIT. По умолчанию транзакции ODBC находятся в режиме автоматической фиксации (если не поддерживаются **SQLSetConnectAttr** и **SQLSetConnectOption** , что маловероятно). Переключение из режима ручной фиксации в режим автоматической фиксации автоматически фиксирует все открытые транзакции в соединении.

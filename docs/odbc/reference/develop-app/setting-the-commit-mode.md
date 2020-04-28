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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f05aaca2349a612cda7c5b6b257e7a1d5a5ea9c5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299824"
---
# <a name="setting-the-commit-mode"></a>Настройка режима фиксации
Приложения указывают режим транзакций с атрибутом подключения SQL_ATTR_AUTOCOMMIT. По умолчанию транзакции ODBC находятся в режиме автоматической фиксации (если не поддерживаются **SQLSetConnectAttr** и **SQLSetConnectOption** , что маловероятно). Переключение из режима ручной фиксации в режим автоматической фиксации автоматически фиксирует все открытые транзакции в соединении.

---
title: Настройка режима коммитса (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299824"
---
# <a name="setting-the-commit-mode"></a>Настройка режима фиксации
Приложения определяют режим транзакции с атрибутом SQL_ATTR_AUTOCOMMIT соединения. По умолчанию транзакции ODBC находятся в режиме автоматического коммита (если только **s'LSetConnectAttr** и **S'LSetConnectOption** не поддерживаются, что маловероятно). Переход из режима ручного коммитса в режим автоматического коммит автоматически автоматически фиксирует любую открытую транзакцию на подключении.

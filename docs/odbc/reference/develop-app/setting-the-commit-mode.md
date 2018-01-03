---
title: "Установка режима фиксации | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 50fbb6064cdf8e36143958d9ef0d6558beeeab21
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-commit-mode"></a>Режим фиксации
Режим транзакции можно указать приложения с помощью атрибута соединения SQL_ATTR_AUTOCOMMIT. По умолчанию транзакции ODBC, в режиме автоматической фиксации (если не **SQLSetConnectAttr** и **SQLSetConnectOption** не поддерживаются, маловероятно, что). Переключение из режима ручной фиксации режим автоматической фиксации автоматически фиксирует любой открытой транзакции в соединении.

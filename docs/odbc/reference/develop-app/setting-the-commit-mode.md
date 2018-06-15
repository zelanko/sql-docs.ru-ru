---
title: Установка режима фиксации | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6d56a85716d88658c6e365484136460f7cce04b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910539"
---
# <a name="setting-the-commit-mode"></a>Режим фиксации
Режим транзакции можно указать приложения с помощью атрибута соединения SQL_ATTR_AUTOCOMMIT. По умолчанию транзакции ODBC, в режиме автоматической фиксации (если не **SQLSetConnectAttr** и **SQLSetConnectOption** не поддерживаются, маловероятно, что). Переключение из режима ручной фиксации режим автоматической фиксации автоматически фиксирует любой открытой транзакции в соединении.

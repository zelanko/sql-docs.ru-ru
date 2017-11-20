---
title: "Установка режима фиксации | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d0c38d70b859b1fb986ebaa366a5396159a95da
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-commit-mode"></a>Режим фиксации
Режим транзакции можно указать приложения с помощью атрибута соединения SQL_ATTR_AUTOCOMMIT. По умолчанию транзакции ODBC, в режиме автоматической фиксации (если не **SQLSetConnectAttr** и **SQLSetConnectOption** не поддерживаются, маловероятно, что). Переключение из режима ручной фиксации режим автоматической фиксации автоматически фиксирует любой открытой транзакции в соединении.


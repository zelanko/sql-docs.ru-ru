---
title: Проверка поддержка функций и особенностей | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82b8a0c2c50e557e055ef14a4ac34a486611304d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="checking-feature-support-and-variability"></a>Проверка поддержка функций и особенностей
Чтобы проверить поддержку функций и особенностей, приложения обычно вызывают **SQLGetInfo**, **SQLGetFunctions**, и **SQLGetTypeInfo**. Отправной точки является драйвер API и SQL грамматики уровни соответствия. Они описывают широкий уровней поддержки. Затем приложение может вызвать **SQLGetInfo** с другими параметрами, чтобы определить, поддержки или изменчивость функций, он должен **SQLGetFunctions** для определения ли функции, он нуждается за возвращенный уровень соответствия поддерживаются, и **SQLGetTypeInfo** для определения, какие типы данных SQL поддерживаются.  
  
 Приложение может определить, поддерживается ли атрибут инструкции или соединения, вызвав **SQLSetStmtAttr** или **SQLSetConnectAttr** с этим атрибутом. Если функция возвращает значение SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, атрибут поддерживается; Если возвращается значение SQL_ERROR и SQLSTATE HYC00 (не реализованы дополнительные функции), атрибут не поддерживается.  
  
 Приложения можно также определить ограниченный объем сведений перед подключением к драйверу, вызвав **SQLDrivers**.

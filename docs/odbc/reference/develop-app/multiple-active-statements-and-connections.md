---
title: "Несколько активных инструкций и подключений | Документы Microsoft"
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
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17be494898610bffba590548767a9d7c3e2915f8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="multiple-active-statements-and-connections"></a>Несколько активных инструкций и соединений
Некоторые драйверы и СУБД Ограничьте число инструкций и соединений, которые могут быть активны одновременно. Эти числа могут быть как один. Дополнительные сведения см. в разделе Параметры SQL_MAX_CONCURRENT_ACTIVITIES и SQL_MAX_DRIVER_CONNECTIONS в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание, функции и [оператор обрабатывает](../../../odbc/reference/develop-app/statement-handles.md) и [ Дескрипторы соединений](../../../odbc/reference/develop-app/connection-handles.md).

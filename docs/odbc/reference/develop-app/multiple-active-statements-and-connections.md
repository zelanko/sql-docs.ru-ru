---
title: Множественные активные инструкции и подключения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76b74ff748a62a401955e4ea4a995f507314124e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942828"
---
# <a name="multiple-active-statements-and-connections"></a>Множественные активные инструкции и подключения
Некоторые драйверы и СУБД Ограничьте число инструкций и соединений, которые могут быть активны одновременно. Эти числа могут быть как один. Дополнительные сведения см. в разделе Параметры SQL_MAX_CONCURRENT_ACTIVITIES и SQL_MAX_DRIVER_CONNECTIONS в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) функции описание, и [оператор обрабатывает](../../../odbc/reference/develop-app/statement-handles.md) и [ Дескрипторы соединений](../../../odbc/reference/develop-app/connection-handles.md).

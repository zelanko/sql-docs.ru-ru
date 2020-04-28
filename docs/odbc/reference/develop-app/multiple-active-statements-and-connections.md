---
title: Множественные активные инструкции и соединения | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8259967942f47b06c50a9043158f8b3b45c58d7a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302433"
---
# <a name="multiple-active-statements-and-connections"></a>Множественные активные инструкции и подключения
Некоторые драйверы и СУБД ограничивают количество инструкций и соединений, которые могут быть активными за один раз. Эти числа могут быть меньше одного. Дополнительные сведения см. в статьях параметры SQL_MAX_CONCURRENT_ACTIVITIES и SQL_MAX_DRIVER_CONNECTIONS в описании функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) , а также [дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md) и [дескрипторы соединения](../../../odbc/reference/develop-app/connection-handles.md).

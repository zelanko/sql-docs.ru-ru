---
description: Множественные активные инструкции и подключения
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
ms.openlocfilehash: 56897dedbd1bf0d96dfa73f75a28db5f1ca46c43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429266"
---
# <a name="multiple-active-statements-and-connections"></a>Множественные активные инструкции и подключения
Некоторые драйверы и СУБД ограничивают количество инструкций и соединений, которые могут быть активными за один раз. Эти числа могут быть меньше одного. Дополнительные сведения см. в статьях параметры SQL_MAX_CONCURRENT_ACTIVITIES и SQL_MAX_DRIVER_CONNECTIONS в описании функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) , а также [дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md) и [дескрипторы соединения](../../../odbc/reference/develop-app/connection-handles.md).

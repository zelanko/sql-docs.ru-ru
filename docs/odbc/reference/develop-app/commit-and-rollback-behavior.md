---
description: Поведение фиксации и отката
title: Поведение фиксации и отката | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 309d28dfb2c97fc8f3d8631edc3f0f7b9db85508
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494672"
---
# <a name="commit-and-rollback-behavior"></a>Поведение фиксации и отката
Распространенное поведение серверных СУБД заключается в закрытии курсоров и отмене подготовленных инструкций при фиксации или откате инструкции. Более вероятно, что для настольных баз данных курсоры открываются и сохраняются подготовленные инструкции. Дополнительные сведения см. в разделе Параметры SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в описании функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) и [воздействие транзакций на курсоры и подготовленные инструкции](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

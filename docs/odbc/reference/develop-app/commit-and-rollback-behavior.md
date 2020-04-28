---
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
ms.openlocfilehash: c67c29b295160a2908152b22c7a349ce4c0f9f50
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299134"
---
# <a name="commit-and-rollback-behavior"></a>Поведение фиксации и отката
Распространенное поведение серверных СУБД заключается в закрытии курсоров и отмене подготовленных инструкций при фиксации или откате инструкции. Более вероятно, что для настольных баз данных курсоры открываются и сохраняются подготовленные инструкции. Дополнительные сведения см. в разделе Параметры SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в описании функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) и [воздействие транзакций на курсоры и подготовленные инструкции](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

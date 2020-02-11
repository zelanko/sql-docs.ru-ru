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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 643d7d4174df66abfcee274c1f987e8f405d19b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083346"
---
# <a name="commit-and-rollback-behavior"></a>Поведение фиксации и отката
Распространенное поведение серверных СУБД заключается в закрытии курсоров и отмене подготовленных инструкций при фиксации или откате инструкции. Более вероятно, что для настольных баз данных курсоры открываются и сохраняются подготовленные инструкции. Дополнительные сведения см. в разделе Параметры SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в описании функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) и [воздействие транзакций на курсоры и подготовленные инструкции](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

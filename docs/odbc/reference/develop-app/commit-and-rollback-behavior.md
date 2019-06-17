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
manager: craigg
ms.openlocfilehash: bad1706e7283c0b0a5111e93c9dfd7ae494c8ef4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125500"
---
# <a name="commit-and-rollback-behavior"></a>Поведение фиксации и отката
Общего поведения между СУБД сервера — закрыть курсоры и отменить подготовленных инструкций, когда оператор выполняется фиксация или откат. Настольных баз данных скорее всего за сохранение курсоров открытыми и подготовленных инструкций. Дополнительные сведения см. в разделе Параметры SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) функции описание и [влияние транзакций на курсоры и подготовленных инструкций](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

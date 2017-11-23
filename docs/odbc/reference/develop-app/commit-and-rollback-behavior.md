---
title: "Фиксации и отката | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f8cecb32a5713f707a885f2004eef0fe13ae47a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="commit-and-rollback-behavior"></a>Фиксации и отката
Закрытие курсоров и отменить подготовленных инструкций, когда выполняется фиксация или откат инструкции — общее поведение между СУБД сервера. Настольных баз данных, скорее всего, сохранение курсоров открытыми и сохранить подготовленных инструкций. Дополнительные сведения см. в разделе Параметры SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) функции описание и [влияние транзакций на курсоры и подготовленных инструкций](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

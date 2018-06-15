---
title: Фиксации и отката | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d859dcaad175ce7f340ecbf8ad8e08492d22b63c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908799"
---
# <a name="commit-and-rollback-behavior"></a>Фиксации и отката
Закрытие курсоров и отменить подготовленных инструкций, когда выполняется фиксация или откат инструкции — общее поведение между СУБД сервера. Настольных баз данных, скорее всего, сохранение курсоров открытыми и сохранить подготовленных инструкций. Дополнительные сведения см. в разделе Параметры SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) функции описание и [влияние транзакций на курсоры и подготовленных инструкций](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

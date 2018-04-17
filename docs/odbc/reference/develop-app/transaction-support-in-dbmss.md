---
title: Поддержка транзакций в СУБД | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4dea29ad82564aa30bdc0c4dbacd3e560ff7e271
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="transaction-support-in-dbmss"></a>Поддержка транзакций в СУБД
Некоторые базы данных, особенно настольных баз данных как dBASE, Paradox и Btrieve, транзакции не поддерживаются. Даже между базами данных, которые поддерживают транзакции нет колебаний тип инструкций SQL может быть в транзакции. Дополнительные сведения см. в разделе параметр SQL_TXN_CAPABLE в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.

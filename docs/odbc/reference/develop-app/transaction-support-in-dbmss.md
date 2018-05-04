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
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0acd20649609d6899edbd4146799d9c002da1c6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="transaction-support-in-dbmss"></a>Поддержка транзакций в СУБД
Некоторые базы данных, особенно настольных баз данных как dBASE, Paradox и Btrieve, транзакции не поддерживаются. Даже между базами данных, которые поддерживают транзакции нет колебаний тип инструкций SQL может быть в транзакции. Дополнительные сведения см. в разделе параметр SQL_TXN_CAPABLE в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.

---
title: Транзакции в ODBC ODBC | Документы Microsoft
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
- transactions [ODBC], about transactions
ms.assetid: 2c8cde03-4bb8-4b35-881b-1ba23da15fbc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9e66a5e92c7aa61820d91f79feffecc35bb62a8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="transactions-in-odbc-odbc"></a>Транзакции в ODBC ODBC
Транзакции в ODBC выполняются на уровне соединения. то есть когда приложение завершает транзакцию, фиксирует или откатывает назад все операции, выполняемые через все дескрипторы инструкций для этого соединения.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Поддержка транзакций](../../../odbc/reference/develop-app/transaction-support.md)  
  
-   [Режим фиксации](../../../odbc/reference/develop-app/commit-mode.md)  
  
-   [Фиксация и откат транзакций](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md)  
  
-   [Влияние транзакций на курсоры и подготовленные инструкции](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)

---
title: Поддержка транзакций в СУБД | Документация Майкрософт
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
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fed5ea04e15002d31e35e25fac405a729929be8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63305690"
---
# <a name="transaction-support-in-dbmss"></a>Поддержка транзакций в СУБД
Некоторые базы данных, особенно настольных систем баз данных, например dBASE, Paradox и Btrieve, транзакции не поддерживаются. Даже среди баз данных, которые поддерживают транзакции нет вариантов в тип инструкций SQL может быть в транзакции. Дополнительные сведения см. в описании параметра SQL_TXN_CAPABLE в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.

---
description: Поддержка транзакций в СУБД
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8e0b3433e0f666af100cce5e72e36b685533b1d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487457"
---
# <a name="transaction-support-in-dbmss"></a>Поддержка транзакций в СУБД
Некоторые базы данных, особенно настольные базы данных, такие как dBASE, Paradox и Btrieve, не поддерживают транзакции. Даже в базах данных, поддерживающих транзакции, существуют различные типы инструкций SQL, которые могут быть в транзакции. Дополнительные сведения см. в описании параметра SQL_TXN_CAPABLE описания функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .

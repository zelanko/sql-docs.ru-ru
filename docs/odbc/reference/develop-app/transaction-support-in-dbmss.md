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
ms.openlocfilehash: 72353e9917996ecacdc5971b4a11f9c73718ba43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037630"
---
# <a name="transaction-support-in-dbmss"></a>Поддержка транзакций в СУБД
Некоторые базы данных, особенно настольные базы данных, такие как dBASE, Paradox и Btrieve, не поддерживают транзакции. Даже в базах данных, поддерживающих транзакции, существуют различные типы инструкций SQL, которые могут быть в транзакции. Дополнительные сведения см. в описании параметра SQL_TXN_CAPABLE описания функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .

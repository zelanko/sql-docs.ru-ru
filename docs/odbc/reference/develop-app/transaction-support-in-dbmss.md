---
title: Поддержка транзакций в DBMSs Документы Майкрософт
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
ms.openlocfilehash: b6da6fdc819d8852aadcd7b672ef06e99d46c0ea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298009"
---
# <a name="transaction-support-in-dbmss"></a>Поддержка транзакций в СУБД
Некоторые базы данных, особенно базы данных настольных компьютеров, такие как dBASE, Paradox и Btrieve, не поддерживают транзакции. Даже среди баз данных, поддерживающих транзакции, существуют различия в том, какие операторы S'L могут быть в транзакции. Для получения более подробной информации в описании функции [S'LGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) можно ознакомиться с SQL_TXN_CAPABLE опцией.

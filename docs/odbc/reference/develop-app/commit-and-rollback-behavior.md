---
title: Поведение фиксации и отката (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c67c29b295160a2908152b22c7a349ce4c0f9f50
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299134"
---
# <a name="commit-and-rollback-behavior"></a>Поведение фиксации и отката
Распространенным поведением среди dBMS сервера является закрытие курсоров и отбрасывание подготовленных инструкций при совершении или откате оператора. Базы данных рабочего стола с большей вероятностью сохраняют курсоры открытыми и сохраняют подготовленные операторы. Для получения более подробной информации ознакомьтесь с вариантами SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в описании функции [S'LGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) и [влиянии транзакций на курсоры и подготовленные заявления.](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)

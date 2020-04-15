---
title: НЕ NULL в CREATE TABLE Заявления (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- not null [ODBC]
- interoperability [ODBC], not null
ms.assetid: 3fb69943-f0c9-4ed2-aa42-20440e37e49d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 490f4a7e49acdad5f919ad21f93d479b03099eb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302392"
---
# <a name="not-null-in-create-table-statements"></a>NOT NULL в инструкциях CREATE TABLE
Некоторые базы данных, и особенно базы данных настольных компьютеров, не поддерживают ограничение столбца **NOT NULL** в заявлениях **CREATE TABLE.** Для получения более подробной информации в описании функции [S'LGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) можно ознакомиться с SQL_NON_NULLABLE_COLUMNS опцией.

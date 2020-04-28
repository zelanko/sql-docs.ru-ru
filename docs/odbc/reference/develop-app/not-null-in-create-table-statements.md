---
title: NOT NULL в операторах CREATE TABLE | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302392"
---
# <a name="not-null-in-create-table-statements"></a>NOT NULL в инструкциях CREATE TABLE
Некоторые базы данных и особенно рабочие базы данных не поддерживают ограничение столбца **NOT NULL** в инструкциях **CREATE TABLE** . Дополнительные сведения см. в описании параметра SQL_NON_NULLABLE_COLUMNS описания функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .

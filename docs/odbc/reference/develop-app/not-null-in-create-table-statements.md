---
description: NOT NULL в инструкциях CREATE TABLE
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
ms.openlocfilehash: 92d066ebb4bd6b712acaa71e0e752b3f0f27a3df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429226"
---
# <a name="not-null-in-create-table-statements"></a>NOT NULL в инструкциях CREATE TABLE
Некоторые базы данных и особенно рабочие базы данных не поддерживают ограничение столбца **NOT NULL** в инструкциях **CREATE TABLE** . Дополнительные сведения см. в описании параметра SQL_NON_NULLABLE_COLUMNS описания функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .

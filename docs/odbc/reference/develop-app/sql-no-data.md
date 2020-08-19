---
description: SQL_NO_DATA
title: SQL_NO_DATA | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb81d6f1fce50a27aba203eec4b78648754010e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424576"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
При использовании ODBC 3. Приложение *x* вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData** в ODBC 2. драйвер *x* для выполнения инструкции UPDATE или DELETE, которая не влияет на строки в источнике данных, драйвер должен возвращать SQL_SUCCESS, а не SQL_NO_DATA. При использовании ODBC 2. *x* или ODBC 3. Приложение *x* , работающее с ODBC 3. драйвер *x* вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData** с одним и тем же результатом, ODBC 3. драйвер *x* должен возвращать SQL_NO_DATA.

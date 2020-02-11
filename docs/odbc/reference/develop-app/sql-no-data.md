---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f899e7a034e1ec5fc967d834caad3a4ccc4caa1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041834"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
При использовании ODBC 3. Приложение *x* вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData** в ODBC 2. драйвер *x* для выполнения инструкции UPDATE или DELETE, которая не влияет на строки в источнике данных, драйвер должен возвращать SQL_SUCCESS, а не SQL_NO_DATA. При использовании ODBC 2. *x* или ODBC 3. Приложение *x* , работающее с ODBC 3. драйвер *x* вызывает **SQLExecDirect**, **SQLExecute**или **метод SQLParamData** с одним и тем же результатом, ODBC 3. драйвер *x* должен возвращать SQL_NO_DATA.

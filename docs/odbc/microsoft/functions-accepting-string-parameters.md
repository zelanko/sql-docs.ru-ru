---
description: Функции, принимающие строковые параметры
title: Функции, принимающие строковые параметры | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], string parameters
- ODBC desktop database drivers [ODBC], string parameters
- Jet-based ODBC drivers [ODBC], string parameters
- functions [ODBC], string parameters
- string parameters [ODBC]
ms.assetid: 869b8421-f71e-4dfd-adce-691bd3012b16
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f634e65260332851d02d2fe67302f03529a6ff7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421858"
---
# <a name="functions-accepting-string-parameters"></a>Функции, принимающие строковые параметры
Все функции, принимающие строковые параметры, будут преобразованы в Юникод. (Будет экспортирована форма "W" функции.) Число байтов преобразуется в число символов для соответствующих API-интерфейсов ODBC. Это относится к следующим функциям:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLColAttributes**  
  
-   **SQLDescribeCol**  
  
-   **SqlError** (заменяется на **SQLGetDiagField**)  
  
-   **SQLExecDirect**  
  
-   **SQLGetCursorName**  
  
-   **SQLSetCursorName**  
  
-   **SQLGetStmtAttr**  
  
-   **SQLGetInfo**  
  
-   **SQLGetStmtOption** ( **SQLGetStmtAttr**)  
  
-   **SQLSetStmtOption** ( **SQLSetStmtAttr**)  
  
-   **SQLGetConnectOption**  
  
-   **SQLSetConnectOption**  
  
-   **SQLGetTypeInfo**  
  
-   **SQLStatistics**  
  
-   **SQLTables**  
  
-   **SQLNativeSQL**  
  
-   **SQLSpecialColumns**  
  
-   **конфигдснекс**  
  
-   **ConfigDSN**

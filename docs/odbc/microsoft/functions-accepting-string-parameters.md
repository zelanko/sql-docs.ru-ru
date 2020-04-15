---
title: Функции, принимающие параметры строки (ru) Документы Майкрософт
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
ms.openlocfilehash: 01d0f143c72f57e946f7fe2bf52a50910d4e56aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286304"
---
# <a name="functions-accepting-string-parameters"></a>Функции, принимающие строковые параметры
Все функции, которые принимают параметры строки, будут преобразованы в Unicode. (Форма функции "W" будет экспортироваться.) Граф байтов преобразуется в подсчет символов для тех применимых ABY ODBC. Это относится к следующим функциям:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **СЗЛКолАтрибуты**  
  
-   **SQLDescribeCol**  
  
-   **S'LОшибка** (заменена **S'LGetDiagField)**  
  
-   **SQLExecDirect**  
  
-   **SQLGetCursorName**  
  
-   **СЗЛСетКурсОрНамейм**  
  
-   **SQLGetStmtAttr**  
  
-   **SQLGetInfo**  
  
-   **СЗЛГетстмтевистрис (становится** **СЗЛГетстмтаттр)**  
  
-   **СЗЛСетстмoption** (становится **S'LsetStmtattr)**  
  
-   **СЗЛГетКоннектОпция**  
  
-   **СЗЛЕтКоннектОпция**  
  
-   **SQLGetTypeInfo**  
  
-   **SQLStatistics**  
  
-   **SQLTables**  
  
-   **СЗЛНаТИЗа**  
  
-   **SQLSpecialColumns**  
  
-   **КонригисНекс**  
  
-   **Конфедерация**

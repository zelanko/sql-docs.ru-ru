---
title: Использование идентификаторов типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f14294b76fc7977de256697c730f7dca31e7a469
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735134"
---
# <a name="using-data-type-identifiers"></a>Использование идентификаторов типов данных
Приложения используют идентификаторы типа данных двумя способами: для описания свои буферы на драйвер и для получения метаданных о результирующем наборе от драйвера, чтобы определить, какой тип C помещает в буфер для хранения данных. Приложения вызывают следующие функции для выполнения следующих задач:  
  
-   **SQLBindParameter**, **SQLBindCol**, и **SQLGetData** - для описания типа данных C буферов приложения.  
  
-   **SQLBindParameter** - для описания типа данных SQL динамических параметров.  
  
-   **SQLColAttribute** и **SQLDescribeCol** — для извлечения типов данных SQL столбцы результирующего набора.  
  
-   **SQLDescribeParameter** — для извлечения типов данных SQL из параметров.  
  
-   **SQLColumns**, **SQLProcedureColumns**, и **SQLSpecialColumns** — для получения различных сведений о схеме типы данных SQL  
  
-   **SQLGetTypeInfo** — для получения списка поддерживаемых типов данных  
  
 Идентификаторы типа данных, хранятся в поле SQL_DESC_CONCISE_TYPE дескриптора. Дескриптор функции **SQLSetDescField** и **SQLSetDescRec** может использоваться с соответствующих типов для выполнения задачи, перечисленные в списке выше. Дополнительные сведения см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).

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
ms.openlocfilehash: e6b8fa49f509c3442c83488ba1e0a5e4a2359d3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654959"
---
# <a name="using-data-type-identifiers"></a>Использование идентификаторов типов данных
Приложения используют идентификаторы типа данных двумя способами: для описания свои буферы на драйвер и для получения метаданных о результирующем наборе от драйвера, чтобы определить, какой тип C помещает в буфер для хранения данных. Приложения вызывают следующие функции для выполнения следующих задач:  
  
-   **SQLBindParameter**, **SQLBindCol**, и **SQLGetData** — для описания типа данных C буферов приложения.  
  
-   **SQLBindParameter** — для описания типа данных SQL динамических параметров.  
  
-   **SQLColAttribute** и **SQLDescribeCol** — для извлечения типов данных SQL столбцы результирующего набора.  
  
-   **SQLDescribeParameter** — для извлечения типов данных SQL из параметров.  
  
-   **SQLColumns**, **SQLProcedureColumns**, и **SQLSpecialColumns** — для получения различных сведений о схеме типы данных SQL  
  
-   **SQLGetTypeInfo** — для получения списка поддерживаемых типов данных  
  
 Идентификаторы типа данных, хранятся в поле SQL_DESC_CONCISE_TYPE дескриптора. Дескриптор функции **SQLSetDescField** и **SQLSetDescRec** может использоваться с соответствующих типов для выполнения задачи, перечисленные в списке выше. Дополнительные сведения см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).

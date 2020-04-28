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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8be8eef0441d48ed03ea6ccf8f656627c1dd9b63
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301425"
---
# <a name="using-data-type-identifiers"></a>Использование идентификаторов типов данных
Приложения используют идентификаторы типов данных двумя способами: для описания их буферов в драйвере и для получения метаданных о результирующем наборе из драйвера, чтобы они могли определить тип буферов C, используемых для хранения данных. Приложения вызывают следующие функции для выполнения следующих задач:  
  
-   **SQLBindParameter**, **SQLBindCol**и **SQLGetData** — описывают тип данных C буферов приложений.  
  
-   **SQLBindParameter** — описание типа данных SQL динамических параметров.  
  
-   **SQLColAttribute** и **SQLDescribeCol** — для получения типов данных SQL для столбцов результирующего набора.  
  
-   **SQLDescribeParameter** — получение типов данных SQL для параметров.  
  
-   **SQLColumns**, **SQLProcedureColumns**и **SQLSPECIALCOLUMNS** — получение типов данных SQL различных сведений о схеме  
  
-   **SQLGetTypeInfo** — получение списка поддерживаемых типов данных  
  
 Идентификаторы типов данных хранятся в SQL_DESC_CONCISE_TYPE поле дескриптора. Функции дескриптора **SQLSetDescField** и **SQLSetDescRec** можно использовать с соответствующими типами для выполнения задач, перечисленных в предыдущем списке. Дополнительные сведения см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).

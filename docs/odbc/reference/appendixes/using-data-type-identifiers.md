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
ms.openlocfilehash: 2b5e9fea64986bf595676540d74bb87a6e62521c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070008"
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

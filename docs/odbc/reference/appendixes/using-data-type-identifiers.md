---
title: Идентификаторы типа данных с помощью | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 283a4b6ed0fe2af5d29b619301f5a5dd283d22b5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-data-type-identifiers"></a>Используя идентификаторы типа данных
Приложения используют идентификаторы типа данных двумя способами: для описания их буферов в драйвер и для получения метаданных о результирующем наборе от драйвера, чтобы определить, какой тип C помещает в буфер для хранения данных. Приложения вызывают следующие функции для выполнения следующих задач:  
  
-   **SQLBindParameter**, **SQLBindCol**, и **SQLGetData** — для описания типов данных C буферов приложения.  
  
-   **SQLBindParameter** — для описания типа данных SQL динамических параметров.  
  
-   **SQLColAttribute** и **SQLDescribeCol** — для извлечения результирующего набора типов данных SQL.  
  
-   **SQLDescribeParameter** — для извлечения параметров типов данных SQL.  
  
-   **SQLColumns**, **SQLProcedureColumns**, и **SQLSpecialColumns** — для получения различных сведений о схеме типы данных SQL  
  
-   **SQLGetTypeInfo** — для получения списка поддерживаемых типов данных  
  
 Идентификаторы типа данных, хранятся в поле SQL_DESC_CONCISE_TYPE дескриптора. Дескриптор функции **SQLSetDescField** и **SQLSetDescRec** может использоваться с типами соответствующих для выполнения задач, перечисленных в списке выше. Дополнительные сведения см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).

---
title: Идентификаторы типа данных с помощью | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a43271157667e98dd9157edb3a2cfd0e85eeee4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907679"
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

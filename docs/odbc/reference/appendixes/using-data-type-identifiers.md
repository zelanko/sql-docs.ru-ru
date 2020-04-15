---
title: Использование идентификаторов типа данных Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301425"
---
# <a name="using-data-type-identifiers"></a>Использование идентификаторов типов данных
Приложения используют идентификаторы типа данных двумя способами: для описания их буферов для драйвера и для получения метаданных о результатах, установленных драйвером, чтобы они могли определить, какой тип c буферов использовать для хранения данных. Приложения называют следующие функции для выполнения следующих задач:  
  
-   **Для**описания типа **SQLBindCol**буферов приложений **SQLGetData** c-данных, для описания типа c-буферов приложений, можно описать тип c-буферов приложений.  
  
-   **S'LBindParameter** - для описания типа динамических параметров данных S'L.  
  
-   Для извлечения типов столбцов набора результатов для получения типов данных, установленных для **s'LColAttribute** и **S'LDescribeCol.**  
  
-   Для извлечения типов параметров данных **S'LDescribeParameter** -  
  
-   Для извлечения в извлечения в из вежливые данные **s'Lcolumns,** **S'LProcedures, S'LProcedures**и **S'LSpecialColumns** - для получения информации о различных схемах  
  
-   **S'LGetTypeInfo** - для получения списка поддерживаемых типов данных  
  
 Идентификаторы типа данных хранятся в SQL_DESC_CONCISE_TYPE поле дескриптора. Функции дескриптора **S'LSetDescField** и **S'LSetDescRec** могут быть использованы с соответствующими типами для выполнения задач, перечисленных в предыдущем списке. Для получения более подробной информации, [см.](../../../odbc/reference/syntax/sqlsetdescfield-function.md)

---
title: "Новые возможности | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], new features in release
- ODBC drivers [ODBC], backward compatibility
- new features [ODBC]
- compatibility [ODBC], new features in release
- ODBC [ODBC], new features
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e2b48097b6c398772e14d2594a583d89e6825e0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="new-features"></a>Новые возможности
Следующие новые функциональные возможности была введена в ODBC 3. *x*. ODBC 3. *x* приложения, работа с ODBC 2*.x* драйвера, не смогут использовать эту функцию. ODBC 3. *x* диспетчер драйверов не сопоставляет эти возможности при работе с ODBC 2*.x* драйвера.  
  
-   Функции, которые принимают дескриптор обработки в качестве аргумента: **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**, и **SQLCopyDesc**.  
  
-   Функции **SQLSetEnvAttr** и **SQLGetEnvAttr**.  
  
-   Использование **SQLAllocHandle** для выделения дескриптора. (Использование **SQLAllocHandle** выделение дескрипторов среды, инструкции и соединения является повторяющиеся, не новые функциональные возможности.)  
  
-   Использование **SQLGetConnectAttr** для получения атрибутов SQL_ATTR_AUTO_IPD соединения. (Использование **SQLSetConnectAttr** для установки, и **SQLGetConnectAttr** для получения, других атрибутах соединения имеет повторяющийся, не новые функциональные возможности.)  
  
-   Использование **SQLSetStmtAttr** для установки, и **SQLGetStmtAttr** для получения следующие атрибуты инструкций. (Использование **SQLSetStmtAttr** для установки, и **SQLGetStmtAttr** для получения, другие атрибуты инструкции является повторяющиеся, не новые функциональные возможности.)  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_ENABLE_AUTO_IPD  
  
     SQL_ATTR_FETCH_BOOKMARK_PTR  
  
     SQL_ATTR_BIND_OFFSET  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     SQL_DESC_PARAM_STATUS_PTR  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR  
  
     SQL_ATTR_PARAMSET_SIZE  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_ROW_ARRAY_SIZE  
  
-   Использование **SQLGetStmtAttr** для получения следующие атрибуты инструкций. (Использование **SQLGetStmtAttr** получить другой инструкции атрибутов является дублированных функций, не новые функциональные возможности.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Использование типа данных C, интервальных типов данных SQL, типы данных BIGINT C и SQL_C_NUMERIC структуру данных.  
  
-   Привязка параметров.  
  
-   Выбирается на основе смещение закладки, например при вызове **SQLFetchScroll** с *FetchOrientation* аргумент SQL_FETCH_BOOKMARK и указать смещение отличное от 0.  
  
-   **SQLFetch** возвращая массив состояния строк, число возвращаемых строк, выборку нескольких строк, следует совместно использовать вызовы с **SQLFetchScroll**и совместно использовать вызовы с **SQLBulkOperations** или **SQLSetPos**. Дополнительные сведения см. следующий раздел, [блочных курсоров, Прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Именованные параметры.  
  
-   Любые ODBC 3. *x*— конкретных **SQLGetInfo** параметры. (Если это ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер вызывает SQL_XXX_CURSOR_ATTRIBUTES1 типы информации, которые произвели замену несколько ODBC 2. *x* типы информации, некоторые сведения могут быть надежным, но некоторые могут быть ненадежными. Дополнительные сведения см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Привязка смещения.  
  
-   Обновление, обновление и удаление с закладки (посредством вызова **SQLBulkOperations**).  
  
-   Вызов **SQLBulkOperations** или **SQLSetPos** в состоянии S5.  
  
-   ROW_NUMBER и равен полей диагностики записи (которой должны обновляться функциями замены **SQLGetDiagField** или **SQLGetDiagRec**).  
  
-   Количество строк, приблизительно.  
  
-   Сведения о предупреждении (SQL_ROW_SUCCESS_WITH_INFO из **SQLFetchScroll**).  
  
-   Закладки переменной длины.  
  
-   Расширенные сведения об ошибке для массивов параметров.  
  
-   Все новые столбцы в результирующих наборах, возвращенных функции каталога.  
  
-   Использование **SQLDescribeCol** и **SQLColAttribute** на столбец 0.  
  
-   Использование любой ODBC 3. *x*— определенного столбца атрибутов в вызове **SQLColAttribute**.  
  
-   Использование нескольких дескрипторов среды.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Блочные курсоры, обратная совместимость для приложений ODBC 3.x и Прокручиваемые курсоры](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)


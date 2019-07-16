---
title: Новые возможности | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], new features in release
- ODBC drivers [ODBC], backward compatibility
- new features [ODBC]
- compatibility [ODBC], new features in release
- ODBC [ODBC], new features
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 74c9a97c2511bc9c9a738b9e63548a9179552489
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086345"
---
# <a name="new-features"></a>Новые возможности
Следующие новые функциональные возможности был введен в ODBC *3.x*. ODBC *3.x* приложение, которое работает с ODBC *2.x* драйвер не сможете использовать эту функцию. ODBC *3.x* диспетчер драйверов не удается сопоставить эти возможности при работе с ODBC *2.x* драйвера.  
  
-   Функции, принимающие дескриптор обрабатывать как аргумент. **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**, и **SQLCopyDesc**.  
  
-   Функции **SQLSetEnvAttr** и **SQLGetEnvAttr**.  
  
-   Использование **SQLAllocHandle** выделения дескриптора дескриптора. (Использование **SQLAllocHandle** выделение дескрипторов среды, подключения и инструкция является повторяющиеся, не новые функциональные возможности.)  
  
-   Использование **SQLGetConnectAttr** для получения атрибутов соединения SQL_ATTR_AUTO_IPD. (Использование **SQLSetConnectAttr** для задания, и **SQLGetConnectAttr** для получения, других атрибутах соединения — повторяющиеся, не новые функциональные возможности.)  
  
-   Использование **SQLSetStmtAttr** для задания, и **SQLGetStmtAttr** для получения, следующие атрибуты инструкций. (Использование **SQLSetStmtAttr** для задания, и **SQLGetStmtAttr** для получения, другие атрибуты инструкции — повторяющиеся, не новые функциональные возможности.)  
  
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
  
-   Использование **SQLGetStmtAttr** для получения следующих атрибутов инструкции. (Использование **SQLGetStmtAttr** для получения другой инструкции атрибутов является продублированные функции, а не новые функциональные возможности.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Использование данных тип интервала C, интервальных типов данных SQL, типы данных BIGINT C и структуре данных SQL_C_NUMERIC.  
  
-   Привязка на уровне строки параметров.  
  
-   Извлекает смещение основе закладки, например, вызов **SQLFetchScroll** с *FetchOrientation* аргумент sql_fetch_bookmark аргумента и указание смещения отличное от 0.  
  
-   **SQLFetch** возвращающему массив состояния строк, число возвращаемых строк, выборку нескольких строк, совместно использовать вызовы с **SQLFetchScroll**и совместно использовать вызовы с **SQLBulkOperations** или **SQLSetPos**. Дополнительные сведения см. следующий раздел, [блочные курсоры, Прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Именованные параметры.  
  
-   Любой из ODBC *3.x*-конкретных **SQLGetInfo** параметры. (Если ODBC *3.x* приложение, которое работает с ODBC *2.x* драйвер вызывает SQL_XXX_CURSOR_ATTRIBUTES1 типы сведений, которые были заменены несколько ODBC *2.x* типы сведений, некоторые данные могут быть надежных, но некоторые могут быть ненадежными. Дополнительные сведения см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Смещения привязки.  
  
-   Обновление, обновление и удаление с закладки (посредством вызова **SQLBulkOperations**).  
  
-   Вызов **SQLBulkOperations** или **SQLSetPos** в состоянии S5.  
  
-   Функции ROW_NUMBER и равен полей диагностики записи (которого нужно извлечь путем замены функции **SQLGetDiagField** или **SQLGetDiagRec**).  
  
-   Количество строк, приблизительно.  
  
-   Сведения о предупреждении (SQL_ROW_SUCCESS_WITH_INFO из **SQLFetchScroll**).  
  
-   Закладки переменной длины.  
  
-   Расширенные сведения об ошибке для массивов параметров.  
  
-   Все новые столбцы в результирующих наборах, возвращаемые функциями каталога.  
  
-   Использование **SQLDescribeCol** и **SQLColAttribute** на столбец 0.  
  
-   Использование любой ODBC *3.x*-атрибуты конкретного столбца в вызове **SQLColAttribute**.  
  
-   Использование нескольких дескрипторов среды.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Блочные курсоры, прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)

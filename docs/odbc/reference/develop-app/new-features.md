---
description: Новые возможности
title: Новые функции | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2015d424e0c755352fa66f3ac67503b612b6982f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429236"
---
# <a name="new-features"></a>Новые возможности
В ODBC *3. x*появились следующие новые функции. Приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , не сможет использовать эту функцию. Диспетчер драйверов ODBC *3. x* не сопоставляет эти функции при работе с драйвером ODBC *2. x* .  
  
-   Функции, которые принимают дескриптор дескриптора в качестве аргумента: **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**и **склкопидеск**.  
  
-   Функции **SQLSetEnvAttr** и **SQLGetEnvAttr**.  
  
-   Использование **функцию SQLAllocHandle** для выделения дескриптора дескриптора. (Использование **функцию SQLAllocHandle** для выделения дескрипторов среды, соединения и инструкции повторяется, а не новых функций.)  
  
-   Использование **SQLGetConnectAttr** для получения атрибутов подключения SQL_ATTR_AUTO_IPD. (Использование **SQLSetConnectAttr** для установки и **SQLGetConnectAttr** для получения, другие атрибуты соединения дублируются, а не новые функции.)  
  
-   Использование **SQLSetStmtAttr** для установки и **SQLGetStmtAttr** для получения следующих атрибутов инструкции. (Использование **SQLSetStmtAttr** для установки и **SQLGetStmtAttr** , чтобы получить, другие атрибуты инструкции дублируются, а не новые функции.)  
  
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
  
-   Использование **SQLGetStmtAttr** для получения следующих атрибутов инструкции. (Использование **SQLGetStmtAttr** для получения других атрибутов инструкции является дубликатом функциональности, а не новыми функциями.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Использование типа данных Interval C, типов данных SQL Interval, типов данных BIGINT C и структуры данных SQL_C_NUMERIC.  
  
-   Привязка параметров на уровне строк.  
  
-   Закладка на основе смещения, например вызов **SQLFetchScroll** с аргументом *фетчориентатион* для SQL_FETCH_BOOKMARK и указание смещения, отличного от 0.  
  
-   **SQLFetch** возвращает массив состояний строк, число извлекаемых строк, получение нескольких строк, объединение вызовов с помощью **SQLFetchScroll**и смешивание вызовов с помощью **SQLBulkOperations** или **SQLSetPos**. Дополнительные сведения см. в следующем разделе: [блочные курсоры, прокручиваемые курсоры и обратная совместимость приложений ODBC 3. x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Именованные параметры.  
  
-   Любой из параметров **SQLGetInfo** , характерных для ODBC *3. x*. (Если приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , вызывает типы сведений SQL_XXX_CURSOR_ATTRIBUTES1, которые заменили несколько типов сведений ODBC *2. x* , некоторые из этих сведений могут быть надежными, но некоторые из них могут быть ненадежными. Дополнительные сведения см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Привязывать смещения.  
  
-   Обновление, обновление и удаление закладками (с помощью вызова **SQLBulkOperations**).  
  
-   Вызов **SQLBulkOperations** или **SQLSetPos** в состоянии S5.  
  
-   Поля ROW_NUMBER и COLUMN_NUMBER в записи диагностики (которые должны быть извлечены функциями замены **SQLGetDiagField** или **SQLGetDiagRec**).  
  
-   Приблизительное количество строк.  
  
-   Сведения о предупреждениях (SQL_ROW_SUCCESS_WITH_INFO из **SQLFetchScroll**).  
  
-   Закладки с переменной длиной.  
  
-   Расширенные сведения об ошибках для массивов параметров.  
  
-   Все новые столбцы в результирующих наборах, возвращаемых функциями каталога.  
  
-   Использование **SQLDescribeCol** и **SQLColAttribute** для столбца 0.  
  
-   Использование атрибутов столбцов, относящихся к ODBC *3. x*, в вызове **SQLColAttribute**.  
  
-   Использование нескольких дескрипторов среды.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Блочные курсоры, прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)

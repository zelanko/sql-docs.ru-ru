---
title: Новые особенности Документы Майкрософт
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
ms.openlocfilehash: b40803dac6c9f296043a8dcac50f9bc69036875a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302402"
---
# <a name="new-features"></a>Новые функции
Следующая новая функциональность была введена в ODBC *3.x*. Приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* не сможет использовать эту функциональность. Менеджер драйвера ODBC *3.x* не отображает эти функции при работе с драйвером ODBC *2.x.*  
  
-   Функции, которые принимают дескриптор ручку в качестве аргумента: **S'LSetDesccField**, **S'LGetDescfield**, **S'LSetDescRec**, **S'LGetDescRec**, и **S'LCopyDesc**.  
  
-   Функциональные функции **S'LSetEnvAttr** и **S'LGetEnvAttr**.  
  
-   Использование **S'LAllocHandle** для выделения дескриптора. (Использование **sLAllocHandle** для выделения декейок среды, соединения и оператора дублируется, а не ново функциональности.)  
  
-   Для получения SQL_ATTR_AUTO_IPD атрибутов подключения используется **s'LGetConnectAttr.** (Для установки, а также для получения других атрибутов соединения, а не новых, функциональности дублируется использование **S'LSetConnectAttr** и **S'LGetConnectAttr.)**  
  
-   Для установки, а также для получения следующих атрибутов оператора, используется **s'LSetStmtAttr** и **S'LGetStmtAttr.** (Использование **S'LSetStmtAttr** для установки, и **S'LGetStmtAttr,** чтобы получить, другие атрибуты оператора дублируется, а не новые, функциональность.)  
  
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
  
-   Использование **S'LGetStmtAttr** для получения следующих атрибутов оператора. (Использование **S'LGetStmtAttr** для получения других атрибутов оператора дублируется функциональностью, а не новой функциональностью.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Использование типа данных интервала C, типов данных интервала S'L, типов данных BIGINT C и SQL_C_NUMERIC структуры данных.  
  
-   Роу-мудрый связывание параметров.  
  
-   Смещение основе закладки извлечения, такие как вызов **S'LFetchScroll** с *FetchOrientation* аргумент SQL_FETCH_BOOKMARK и указывая смещения, кроме 0.  
  
-   **S'LFetch** возвращает массив состояния строки, количество строк, извлеченных, извлечения нескольких строк, перемешивания вызовов с **S'LFetchScroll**, и перемешивание вызовов с **S'LBulkOperations** или **S'LSetPos**. Для получения дополнительной информации смотрите следующий раздел, [Блок Курсоры, Прокрутки Cursors, и обратной совместимости для ODBC 3.x приложений](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Именованные параметры.  
  
-   Любой из вариантов ODBC *3.x-специфический* **S'LGetInfo.** (Если приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* вызывает SQL_XXX_CURSOR_ATTRIBUTES1 типов информации, которые заменили несколько типов информации ODBC *2.x,* некоторые сведения могут быть надежными, но некоторые могут быть ненадежными. Для получения более подробной информации, [см.](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   Связать смещения.  
  
-   Обновление, обновление и удаляние закладками (через звонок в **S'LBulkOperations).**  
  
-   Вызов **S'LBulkOperations** или **S'LSetPos** в состоянии S5.  
  
-   В ROW_NUMBER и COLUMN_NUMBER полях в диагностической записи (которые должны быть извлечены с помощью функций замены **S'LGetDiagField** или **S'LGetDiagRec).**  
  
-   Приблизительные значения строки.  
  
-   Предупреждающая информация (SQL_ROW_SUCCESS_WITH_INFO от **S'LFetchScroll).**  
  
-   Закладки переменной длины.  
  
-   Расширенная информация об ошибке для массивов параметров.  
  
-   Все новые столбцы в наборах результатов, возвращенные функциями каталога.  
  
-   Использование **S'LDescribeCol** и **S'LColAttribute** в столбце 0.  
  
-   Использование любых атрибутов столбца ODBC *3.x*в вызове на **s'LColAttribute**.  
  
-   Использование нескольких обрабатываек среды.  
  
 Этот раздел содержит следующую тему.  
  
-   [Блочные курсоры, прокручиваемые курсоры и обратная совместимость для приложений ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)

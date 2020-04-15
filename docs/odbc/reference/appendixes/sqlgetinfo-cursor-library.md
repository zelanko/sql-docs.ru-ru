---
title: СЗЛГетИнфо (Библиотека Курзора) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Cursor Library
ms.assetid: 1b4d220d-2c07-4f56-987e-36813bb1a6ce
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9067fd8b33cb2408f1ef6f0e58603eb4f1f7eb09
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307815"
---
# <a name="sqlgetinfo-cursor-library"></a>SQLGetInfo (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LGetInfo** в библиотеке курсоров. Для получения общей информации о **s'LGetInfo,** см. [SQLGetInfo Function](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
 Библиотека курсора возвращает значения для следующих значений *InfoType* (&#124; представляет собой битрачную ИЛИ); для всех других значений *InfoType,* он называет **S'LGetInfo** в драйвере.  
  
|*InfoType*|Возвращаемое значение|  
|----------------|--------------------|  
|SQL_BOOKMARK_PERSISTENCE|SQL_BP_SCROLL|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|0|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|0|  
|SQL_FETCH_DIRECTION|SQL_FD_FETCH_ABSOLUTE &#124; SQL_FD_FETCH_FIRST SQL_FD_FETCH_FIRST SQL_FD_FETCH_LAST &#124; &#124; &#124; &#124; &#124; SQL_FD_FETCH_NEXT SQL_FD_FETCH_BOOKMARK SQL_FD_FETCH_RELATIVE &#124; SQL_FD_FETCH_PRIOR &#124;, &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124;|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &#124; SQL_CA1_ABSOLUTE &#124; SQL_CA1_RELATIVE &#124; SQL_CA1_LOCK_NO_CHANGE &#124; SQL_CA1_POS_POSITION &#124; SQL_CA1_POSITIONED_DELETE &#124; SQL_CA1_POSITIONED_UPDATE &#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &#124; SQL_CA2_OPT_VALUES_CONCURRENCY &#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_GETDATA_EXTENSIONS|SQL_GD_BLOCK &#124; любые значения, возвращенные **примечанием драйвера:** При извлечении данных с **помощью S'LFetchScroll,** **S'LGetData** поддерживает функциональность, указанную с SQL_GD_ANY_COLUMN и SQL_GD_BOUND битмаски.|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES1|0|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES2|0|  
|SQL_LOCK_TYPES|SQL_LCK_NO_CHANGE|  
|SQL_STATIC_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &#124; SQL_CA1_ABSOLUTE &#124; SQL_CA1_RELATIVE &#124; SQL_CA1_BOOKMARK &#124; SQL_CA1_LOCK_NO_CHANGE &#124; SQL_CA1_POS_POSITION &#124; SQL_CA1_POSITIONED_DELETE &#124; SQL_CA1_POSITIONED_UPDATE &#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_STATIC_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &#124; SQL_CA2_OPT_VALUES_ SQL_CA2_SENSITIVITY_UPDATES &#124; КОНВАЛЮТ|  
|SQL_POS_OPERATIONS|SQL_POS_POSITION|  
|SQL_POSITIONED_STATEMENTS|SQL_PS_POSITIONED_DELETE &#124; SQL_PS_POSITIONED_UPDATE &#124; SQL_PS_SELECT_FOR_UPDATE|  
|SQL_ROW_UPDATES|«Y»|  
|SQL_SCROLL_CONCURRENCY|SQL_SCCO_READ_ONLY &#124; SQL_SCCO_OPT_VALUES|  
|SQL_SCROLL_OPTIONS|SQL_SO_FORWARD_ONLY &#124; SQL_SO_STATIC|  
|SQL_STATIC_SENSITIVITY|SQL_SS_UPDATES|  
  
 Используется только тогда, когда библиотека курсора используется с драйвером ODBC 2.x.  
  
> [!IMPORTANT]  
>  Библиотека курсора реализует то же поведение курсора при совершении транзакций или откате в качестве источника данных. То есть совершение или откат транзакции, либо позвонив в **S'LEndTran,** либо используя атрибут SQL_ATTR_AUTOCOMMIT соединения, может привести к удалению источника данных и закрытию курсоров для всех инструкций по подключению. Для получения более подробной информаци SQL_CURSOR_ROLLBACK_BEHAVIOR [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)SQL_CURSOR_COMMIT_BEHAVIORи, см.

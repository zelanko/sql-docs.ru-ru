---
title: SQLGetInfo (библиотека курсоров) | Документы Microsoft
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
- SQLGetInfo function [ODBC], Cursor Library
ms.assetid: 1b4d220d-2c07-4f56-987e-36813bb1a6ce
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a52b5f5c9ab334ba6390793255f55754b8e088b4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetinfo-cursor-library"></a>SQLGetInfo (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLGetInfo** функции в библиотеку курсоров. Общие сведения о **SQLGetInfo**, в разделе [SQLGetInfo, функция](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 Библиотека курсоров возвращает значения для следующих значений *свойство* (&#124; представляет побитовое или); для всех остальных значений *свойство*, он вызывает **SQLGetInfo** в драйвере.  
  
|*Свойство*|Возвращаемое значение|  
|----------------|--------------------|  
|SQL_BOOKMARK_PERSISTENCE|SQL_BP_SCROLL|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|0|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|0|  
|SQL_FETCH_DIRECTION [1]|SQL_FD_FETCH_ABSOLUTE &AMP;#124; SQL_FD_FETCH_FIRST &AMP;#124; SQL_FD_FETCH_LAST &AMP;#124; SQL_FD_FETCH_NEXT &AMP;#124; SQL_FD_FETCH_PRIOR &AMP;#124; SQL_FD_FETCH_RELATIVE &AMP;#124; SQL_FD_FETCH_BOOKMARK|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &AMP;#124; SQL_CA1_ABSOLUTE &AMP;#124; SQL_CA1_RELATIVE &AMP;#124; SQL_CA1_LOCK_NO_CHANGE &AMP;#124; SQL_CA1_POS_POSITION &AMP;#124; SQL_CA1_POSITIONED_DELETE &AMP;#124; SQL_CA1_POSITIONED_UPDATE &AMP;#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &AMP;#124; SQL_CA2_OPT_VALUES_CONCURRENCY &AMP;#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_GETDATA_EXTENSIONS|SQL_GD_BLOCK &#124; любые значения, возвращенные с помощью драйвера **Примечание:** при получении данных с **SQLFetchScroll**, **SQLGetData** поддерживает функции, указанные битовой маски SQL_GD_ANY_COLUMN и SQL_GD_BOUND.|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES1|0|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES2|0|  
|SQL_LOCK_TYPES [1]|SQL_LCK_NO_CHANGE|  
|SQL_STATIC_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &AMP;#124; SQL_CA1_ABSOLUTE &AMP;#124; SQL_CA1_RELATIVE &AMP;#124; SQL_CA1_BOOKMARK &AMP;#124; SQL_CA1_LOCK_NO_CHANGE &AMP;#124; SQL_CA1_POS_POSITION &AMP;#124; SQL_CA1_POSITIONED_DELETE &AMP;#124; SQL_CA1_POSITIONED_UPDATE &AMP;#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_STATIC_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &AMP;#124; SQL_CA2_OPT_VALUES_ ПАРАЛЛЕЛИЗМА &AMP;#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_POS_OPERATIONS [1]|SQL_POS_POSITION|  
|SQL_POSITIONED_STATEMENTS [1]|SQL_PS_POSITIONED_DELETE &AMP;#124; SQL_PS_POSITIONED_UPDATE &AMP;#124; SQL_PS_SELECT_FOR_UPDATE|  
|SQL_ROW_UPDATES|«Y»|  
|SQL_SCROLL_CONCURRENCY [1]|SQL_SCCO_READ_ONLY &AMP;#124; SQL_SCCO_OPT_VALUES|  
|SQL_SCROLL_OPTIONS|SQL_SO_FORWARD_ONLY &AMP;#124; SQL_SO_STATIC|  
|SQL_STATIC_SENSITIVITY [1]|SQL_SS_UPDATES|  
  
 [1] используется только при использовании библиотеки курсоров с помощью драйвера ODBC 2.x.  
  
> [!IMPORTANT]  
>  Библиотека курсоров реализует такое же поведение курсора после фиксации или отката в качестве источника данных транзакций. То есть, фиксация или откат транзакции, либо путем вызова **SQLEndTran** или с помощью атрибута соединения SQL_ATTR_AUTOCOMMIT, могут привести к источнику данных для удаления планов доступа и закрытие курсоров для всех инструкций для подключения. Дополнительные сведения см. в разделе типы информации SQL_CURSOR_COMMIT_BEHAVIOR и SQL_CURSOR_ROLLBACK_BEHAVIOR в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).

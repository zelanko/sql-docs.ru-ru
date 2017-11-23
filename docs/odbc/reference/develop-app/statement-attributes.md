---
title: "Атрибуты инструкции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 36cc6b00223185a5a1e21708109842384c6ecb1e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="statement-attributes"></a>Атрибуты инструкции
Атрибуты инструкции представляют собой характеристики инструкции. Например установлены ли использование закладок и что тип курсора для использования с результатом инструкции являются атрибуты инструкции.  
  
 Атрибуты инструкции устанавливаются с помощью **SQLSetStmtAttr** и их текущие настройки извлекаются с помощью **SQLGetStmtAttr**. Нет необходимости устанавливать что приложения атрибуты; все атрибуты инструкции имеют значения по умолчанию, некоторые из которых зависят от конкретного драйвера.  
  
 Если атрибут инструкции можно задать зависит от самого атрибута. Необходимо задать атрибуты инструкции SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR и SQL_ATTR_USE_BOOKMARKS перед выполнением инструкции. Атрибуты инструкции атрибуту SQL_ATTR_ASYNC_ENABLE и SQL_ATTR_NOSCAN в любое время можно установить, но не применяются, пока не будет снова используется инструкция. Значения SQL_ATTR_MAX_LENGTH и SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT атрибуты инструкции, которые можно задать в любое время, но относящиеся к драйверу ли они применяются, прежде чем снова используется инструкция. Остальные атрибуты инструкции можно задать в любое время.  
  
> [!NOTE]  
>  Возможность установки атрибутов инструкции на уровне соединения путем вызова **SQLSetConnectAttr** был объявлен устаревшим в ODBC 3. *x*. ODBC 3. *x* приложения никогда не следует устанавливать атрибуты инструкции на уровне соединения. ODBC 3. *x* драйверы должен поддерживать эту функциональность, только если они должны работать с ODBC 2. *x* приложений. Дополнительные сведения см. в разделе [SQLSetConnectOption сопоставление](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
>   
>  Исключением является SQL_ATTR_METADATA_ID и атрибуту SQL_ATTR_ASYNC_ENABLE атрибуты, которые являются атрибуты соединения и атрибуты инструкции и можно задать либо на уровне соединения или на уровне инструкции.  
>   
>  Ни один из атрибутов инструкции, представленные в ODBC 3. *x* (SQL_ATTR_METADATA_ID) может быть задано на уровне соединения.  
  
 Дополнительные сведения см. в разделе [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) описание функции.

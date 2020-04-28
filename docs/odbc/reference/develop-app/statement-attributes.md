---
title: Атрибуты инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec24cc43e8c57e47ddda9f20fac1807f42453e84
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299647"
---
# <a name="statement-attributes"></a>Атрибуты инструкции
Атрибуты инструкции являются характеристиками инструкции. Например, следует ли использовать закладки и какой тип курсора будет использоваться с результирующим набором инструкции, это атрибуты инструкции.  
  
 Атрибуты инструкции задаются с помощью **SQLSetStmtAttr** и их текущих параметров, полученных с помощью **SQLGetStmtAttr**. Приложению не требуется устанавливать какие-либо атрибуты инструкции; все атрибуты инструкции имеют значения по умолчанию, некоторые из которых относятся к конкретному драйверу.  
  
 Если атрибут инструкции может быть установлен, зависит от самого атрибута. Перед выполнением инструкции необходимо задать атрибуты операторов SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR и SQL_ATTR_USE_BOOKMARKS. Атрибуты инструкций SQL_ATTR_ASYNC_ENABLE и SQL_ATTR_NOSCAN могут быть установлены в любое время, но не применяются, пока инструкция не будет использована снова. Атрибуты инструкций SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS и SQL_ATTR_QUERY_TIMEOUT могут быть установлены в любое время, но они относятся к конкретному драйверу, независимо от того, применяются ли они до повторного использования инструкции. Остальные атрибуты инструкции можно задать в любое время.  
  
> [!NOTE]  
>  Возможность установки атрибутов инструкций на уровне соединения путем вызова **SQLSetConnectAttr** в ODBC 3 является нерекомендуемой. *x*. ODBC 3. приложения *x* никогда не должны задавать атрибуты инструкций на уровне соединения. ODBC 3. драйверы *x* должны поддерживать эту функцию только в том случае, если они должны работать с ODBC 2. приложения *x* . Дополнительные сведения см. в разделе [сопоставление SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) в приложении G: рекомендации по драйверу для обеспечения обратной совместимости.  
>   
>  Исключением является SQL_ATTR_METADATA_ID и SQL_ATTR_ASYNC_ENABLE атрибуты, которые являются атрибутами соединения и атрибутами инструкций и могут быть заданы либо на уровне соединения, либо на уровне инструкции.  
>   
>  Ни один из атрибутов инструкции не появился в ODBC 3. *x* (кроме SQL_ATTR_METADATA_ID) можно задать на уровне соединения.  
  
 Дополнительные сведения см. в описании функции [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) .

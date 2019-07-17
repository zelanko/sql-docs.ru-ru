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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c74f1a79ef79b682bc2900d671e07bbe34c4dbf5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107273"
---
# <a name="statement-attributes"></a>Атрибуты инструкции
Атрибуты инструкции представляют собой характеристики инструкции. Например атрибуты инструкции, ли использование закладок и новые разновидности курсор для использования с результатом оператор набора.  
  
 Атрибуты инструкции устанавливаются с помощью **SQLSetStmtAttr** и их текущие настройки извлекаются с помощью **SQLGetStmtAttr**. Нет необходимости, что приложения устанавливать атрибуты; все атрибуты инструкции имеют значения по умолчанию, некоторые из них специфические для драйвера.  
  
 Когда можно задать атрибут инструкции зависит от самого атрибута. Атрибуты инструкции SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR и SQL_ATTR_USE_BOOKMARKS необходимо задать перед выполнением инструкции. Атрибуты инструкции атрибуту SQL_ATTR_ASYNC_ENABLE и SQL_ATTR_NOSCAN можно настроить в любое время, но не применяются, пока не будет снова используется инструкция. В любое время можно установить значения SQL_ATTR_MAX_LENGTH и SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT атрибуты инструкции, но относящиеся к драйверу ли они применяются, прежде чем снова используется инструкция. Остальные атрибуты инструкции можно задать в любое время.  
  
> [!NOTE]  
>  Возможность устанавливать атрибуты инструкции на уровне соединения, вызвав **SQLSetConnectAttr** был объявлен устаревшим в ODBC 3. *x*. ODBC 3. *x* приложения никогда не следует устанавливать атрибуты инструкции на уровне соединения. ODBC 3. *x* драйверы должен поддерживать эту функцию, только если они должны работать с ODBC 2. *x* приложений. Дополнительные сведения см. в разделе [сопоставление SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) в приложении G: Рекомендации по драйверов для обеспечения обратной совместимости.  
>   
>  Исключением является SQL_ATTR_METADATA_ID и атрибуту SQL_ATTR_ASYNC_ENABLE атрибуты, которые являются атрибуты соединения и атрибуты инструкции и можно задать либо на уровне соединения или на уровне инструкции.  
>   
>  Ни один из атрибутов инструкции, представленные в ODBC 3. *x* (за исключением SQL_ATTR_METADATA_ID) можно задать на уровне соединения.  
  
 Дополнительные сведения см. в разделе [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) описание функции.

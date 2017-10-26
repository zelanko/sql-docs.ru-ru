---
title: "Вызов SQLSetPos для вставки данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e9d768ea5c16b199dc316726cb425b75d409bf1f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="calling-sqlsetpos-to-insert-data"></a>Вызов SQLSetPos для вставки данных
Когда ODBC 2. *x* приложения, работа с ODBC 3*.x* драйвер вызывает **SQLSetPos** с *операции* аргумент SQL_ADD, диспетчер драйверов Этот вызов не соответствует **SQLBulkOperations**. Если ODBC 3*.x* драйвер должен работать с приложениями, которые вызывают **SQLSetPos** с SQL_ADD, драйвер должен поддерживать этой операции.  
  
 Одно из основных отличий в поведении при **SQLSetPos** вызове с параметром SQL_ADD возникает при вызове в состоянии S6. В ODBC 2. *x*, драйвер возвращал S1010 при **SQLSetPos** был вызван с SQL_ADD в состоянии S6 (после курсор, было располагается с **SQLFetch**). В ODBC 3*.x*, **SQLBulkOperations** с *операции* из SQL_ADD может вызываться в состоянии S6. Это второй основное различие в поведении **SQLBulkOperations** с *операции* SQL_ADD может быть вызван в состоянии S5, тогда как **SQLSetPos** с ** Операция** из SQL_ADD невозможно. Для переходов оператора, может возникнуть по тем же вызовом в ODBC 3*.x*, в разделе [таблицами приложение б: ODBC состояний перехода](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).


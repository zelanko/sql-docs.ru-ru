---
title: "Компоненты, которые должны ожидать | Документы Microsoft"
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
- interoperability [ODBC], writing interoperable applications
ms.assetid: 0fb1693b-11c3-43b1-bb16-c3323b7b2d45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 89e348d084f150bdcb2d74f4d4dd561816fc351f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="features-to-watch-for"></a>Компоненты, которые должны ожидать
В этом разделе описываются некоторые функции, которые разработчики часто предпринять должное. На самом деле эти функции существенно различаться по поддержке и способ поддержки между СУБД; сбой кода для них может вызвать проблемы с возможностью взаимодействия приложений.  
  
 В этом разделе не включает все компоненты, которые разработчики приложений должны учесть. Эти сведения в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md), и [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) функции описания, [грамматику SQL приложение C:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)и разделах данного руководства, посвященные каждого компонента.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Номер версии](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Несколько активных инструкций и соединений](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Поддержка транзакций в СУБД](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Фиксации и отката](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [NOT NULL в инструкции CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Поддерживаемые типы данных](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [SQL-грамматику ODBC](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Пакетная обработка](../../../odbc/reference/develop-app/batch-processing.md)


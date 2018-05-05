---
title: Компоненты, которые должны ожидать | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], writing interoperable applications
ms.assetid: 0fb1693b-11c3-43b1-bb16-c3323b7b2d45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5ccdd8349b292e6a752d205dd5dabdca596ba46
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="features-to-watch-for"></a>Компоненты, которые должны ожидать
В этом разделе описываются некоторые функции, которые разработчики часто предпринять должное. На самом деле эти функции существенно различаться по поддержке и способ поддержки между СУБД; сбой кода для них может вызвать проблемы с возможностью взаимодействия приложений.  
  
 В этом разделе не включает все компоненты, которые разработчики приложений должны учесть. Эти сведения в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md), и [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) функции описания, [грамматику SQL приложение C:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)и разделах данного руководства, посвященные каждого компонента.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Номер версии](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Множественные активные инструкции и подключения](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Поддержка транзакций в СУБД](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Поведение фиксации и отката](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [NOT NULL в инструкциях CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Поддерживаемые типы данных](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [Грамматика SQL (ODBC)](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Пакетная обработка](../../../odbc/reference/develop-app/batch-processing.md)

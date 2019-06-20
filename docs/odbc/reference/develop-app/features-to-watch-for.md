---
title: Функции требуется контролировать | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], writing interoperable applications
ms.assetid: 0fb1693b-11c3-43b1-bb16-c3323b7b2d45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe5bce7a8a13c7296ce08f84ea4b0c60c2eb5261
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061612"
---
# <a name="features-to-watch-for"></a>Компоненты, которые требуется контролировать
В этом разделе описывается ряд функций, которые разработчики часто принимают как должное. На самом деле эти функции существенно различаться поддержки и способ поддержки между СУБД; Сбой в код для них может вызвать проблемы в приложениях с возможностью взаимодействия.  
  
 В этом разделе не включает все функции, которые необходимо учитывать разработчикам приложений. Дополнительные сведения см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md), и [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) функции описания, [приложение в: Грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)и разделах данного руководства, посвященные каждого компонента.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Номер версии](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Множественные активные инструкции и подключения](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Поддержка транзакций в СУБД](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Поведение фиксации и отката](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [NOT NULL в инструкциях CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Поддерживаемые типы данных](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [Грамматика SQL (ODBC)](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Пакетная обработка](../../../odbc/reference/develop-app/batch-processing.md)

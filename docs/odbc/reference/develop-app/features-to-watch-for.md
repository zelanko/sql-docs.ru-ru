---
title: Отслеживаемые функции | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10fa5df8a47837e92d4215f558d52711a0df3440
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305685"
---
# <a name="features-to-watch-for"></a>Компоненты, которые требуется контролировать
В этом разделе описывается ряд функций, которые часто требуется разработчикам приложений для предоставления. На самом деле, эти функции значительно отличаются в поддержке и способе поддержки различных СУБД. невозможность кода для них может вызвать проблемы в взаимодействующих приложениях.  
  
 В этом разделе не перечислены все функции, которые необходимо учитывать разработчикам приложений. Дополнительные сведения см. в описании функций [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)и [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) , [Приложение C: грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)и разделы руководства, посвященные каждому компоненту.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Номер версии](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Множественные активные инструкции и подключения](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Поддержка транзакций в СУБД](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Поведение фиксации и отката](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [NOT NULL в инструкциях CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Поддерживаемые типы данных](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [Грамматика SQL (ODBC)](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Пакетная обработка](../../../odbc/reference/develop-app/batch-processing.md)

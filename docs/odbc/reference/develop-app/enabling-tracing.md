---
title: Включение трассировки | Документы Microsoft
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
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78bac3ff523635a8624b5db025d1036d3facd0d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="enabling-tracing"></a>Включение трассировки
Трассировку можно включить в следующих трех способов:  
  
-   Задать **трассировки** и **TraceFile** ключевые слова в записи реестра Odbc.ini. Это включает или отключает трассировку, когда **SQLAllocHandle** с *HandleType* вызывается установленным в значение sql_handle_env. Эти параметры задаются на вкладке "Трассировка" диалоговое окно администратора источника данных ODBC, во время настройки источника данных. Дополнительные сведения см. в разделе [записи реестра для источников данных](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Вызовите **SQLSetConnectAttr** для задания атрибута соединения SQL_ATTR_TRACE SQL_OPT_TRACE_ON. Это включает или отключает трассировку в течение всего соединения. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) описание функции.  
  
-   Используйте **ODBCSharedTraceFlag** для выключать трассировку динамически. (Дополнительные сведения см. в разделе Далее [динамической трассировки](../../../odbc/reference/develop-app/dynamic-tracing.md).)

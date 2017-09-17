---
title: "Включение трассировки | Документы Microsoft"
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
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d80f7e70915c11a3a45f90d2821b9c1bd137d9dd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="enabling-tracing"></a>Включение трассировки
Трассировку можно включить в следующих трех способов:  
  
-   Задать **трассировки** и **TraceFile** ключевые слова в записи реестра Odbc.ini. Это включает или отключает трассировку, когда **SQLAllocHandle** с *HandleType* вызывается установленным в значение sql_handle_env. Эти параметры задаются на вкладке "Трассировка" диалоговое окно администратора источника данных ODBC, во время настройки источника данных. Дополнительные сведения см. в разделе [записи реестра для источников данных](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Вызовите **SQLSetConnectAttr** для задания атрибута соединения SQL_ATTR_TRACE SQL_OPT_TRACE_ON. Это включает или отключает трассировку в течение всего соединения. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) описание функции.  
  
-   Используйте **ODBCSharedTraceFlag** для выключать трассировку динамически. (Дополнительные сведения см. в разделе Далее [динамической трассировки](../../../odbc/reference/develop-app/dynamic-tracing.md).)

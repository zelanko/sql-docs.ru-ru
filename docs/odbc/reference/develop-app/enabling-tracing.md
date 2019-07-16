---
title: Включение трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 24f80e0e81e4be8895d59256492b868c53aab7b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046792"
---
# <a name="enabling-tracing"></a>Включение трассировки
Трассировку можно включить в следующих трех способов:  
  
-   Задайте **трассировки** и **TraceFile** ключевые слова в записи реестра Odbc.ini. Это включает или отключает трассировку, когда **SQLAllocHandle** с *HandleType* SQL_HANDLE_ENV, называется. Эти параметры задаются на вкладке "Трассировка" диалоговое окно администратора источника данных ODBC, отображаться во время настройки источника данных. Дополнительные сведения см. в разделе [записи реестра для источников данных](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Вызовите **SQLSetConnectAttr** присвоить атрибут соединения SQL_ATTR_TRACE SQL_OPT_TRACE_ON. Это включает или отключает трассировку в течение всего соединения. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) описание функции.  
  
-   Используйте **ODBCSharedTraceFlag** для выключать трассировку динамически. (Дополнительные сведения см. следующий раздел, [динамического трассировки](../../../odbc/reference/develop-app/dynamic-tracing.md).)

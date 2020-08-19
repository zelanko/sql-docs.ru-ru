---
description: Включение трассировки
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af9a78989a80124fb9a7f475edf17022e7942bde
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482987"
---
# <a name="enabling-tracing"></a>Включение трассировки
Трассировку можно включить следующими тремя способами.  
  
-   Задайте ключевые слова **Trace** и **TraceFile** в записи реестра Odbc.ini. Это включает или отключает трассировку при вызове **функцию SQLAllocHandle** с *параметром handletype* SQL_HANDLE_ENV. Эти параметры задаются на вкладке трассировка диалогового окна Администратор источников данных ODBC, отображаемого во время настройки источника данных. Дополнительные сведения см. в разделе [записи реестра для источников данных](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Вызовите **SQLSetConnectAttr** , чтобы задать для атрибута подключения SQL_ATTR_TRACE значение SQL_OPT_TRACE_ON. Это включает или отключает трассировку на время соединения. Дополнительные сведения см. в описании функции [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) .  
  
-   Используйте **одбкшаредтрацефлаг** , чтобы включить или отключить трассировку динамически. (Дополнительные сведения см. в следующем разделе [Динамическая трассировка](../../../odbc/reference/develop-app/dynamic-tracing.md).)

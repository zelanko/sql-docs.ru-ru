---
title: Включение трассировки Документы Майкрософт
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
ms.openlocfilehash: 80bd4023a0260b67d11d7b4ded1bb810b81e0ab2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287354"
---
# <a name="enabling-tracing"></a>Включение трассировки
Отслеживание может быть включено следующими тремя способами:  
  
-   Установите ключевые слова **Trace** и **TraceFile** в регистрации Odbc.ini. Это позволяет или отсчитывает отслеживание при вызове **S'LAllocHandle** с *помощью SQL_HANDLE_ENV.* Эти параметры установлены во вкладке «Отслеживание» в диалоговом окне администратора источников данных ODBC Data Administrator, отображаемое при настройке источника данных. Для получения дополнительной информации смотрите [записи реестра для источников данных](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Позвоните в **S'LSetConnectAttr,** чтобы настроить атрибут SQL_ATTR_TRACE соединения на SQL_OPT_TRACE_ON. Это позволяет или отсчитывает отслеживание на время соединения. Для получения более подробной информации ознакомьтесь с описанием функции [S'LSetConnectAttr.](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
-   Используйте **ODBCSharedTraceFlag,** чтобы включить или выключить трассировку. (Для получения дополнительной информации, см. следующую тему, [динамическая трассировка](../../../odbc/reference/develop-app/dynamic-tracing.md).)

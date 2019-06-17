---
title: Явно выделенные дескрипторы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fbec69e0d984d843abc2b8754e111a1199c79a5a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049793"
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенные дескрипторы
Приложения явным образом можно выделить дескриптор приложений для подключения в любое время, в которой он подключен к базе данных. Путем указания этого дескриптора как атрибут инструкцию обработки с помощью **SQLSetStmtAttr**, приложение направляет драйвер для использования этого дескриптора вместо соответствующих неявно выделенные приложения дескрипторы. Приложение нельзя указать альтернативные реализации дескрипторов.  
  
 Приложение можно связать дескриптор явно выделенные с более одной инструкции. Только в том случае, если приложение фактически подключено к базе данных дескриптор может быть явным образом выделенного дескриптора. Приложение можно освободить таких дескриптор явно или неявно, освобождая его подключения.

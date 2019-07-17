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
ms.openlocfilehash: 5808265a9ab70b9947cea64fef790497c7229da8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069931"
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенные дескрипторы
Приложения явным образом можно выделить дескриптор приложений для подключения в любое время, в которой он подключен к базе данных. Путем указания этого дескриптора как атрибут инструкцию обработки с помощью **SQLSetStmtAttr**, приложение направляет драйвер для использования этого дескриптора вместо соответствующих неявно выделенные приложения дескрипторы. Приложение нельзя указать альтернативные реализации дескрипторов.  
  
 Приложение можно связать дескриптор явно выделенные с более одной инструкции. Только в том случае, если приложение фактически подключено к базе данных дескриптор может быть явным образом выделенного дескриптора. Приложение можно освободить таких дескриптор явно или неявно, освобождая его подключения.

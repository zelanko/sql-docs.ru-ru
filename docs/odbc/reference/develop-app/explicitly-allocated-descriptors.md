---
description: Явно выделенные дескрипторы
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7215d17a7156419f08bbd73528c468d7b6355b94
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461486"
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенные дескрипторы
Приложение может явно выделить дескриптор приложения для соединения в любое время, когда оно подключено к базе данных. Если указать этот дескриптор дескриптора как атрибут дескриптора инструкции с помощью **SQLSetStmtAttr**, приложение направляет драйвер на использование этого дескриптора вместо соответствующих неявно выделенных дескрипторов приложений. Приложение не может указывать альтернативные дескрипторы реализации.  
  
 Приложение может связать явно выделенный дескриптор с более чем одной инструкцией. Дескриптор может быть явно выделенным дескриптором, только если приложение действительно подключено к базе данных. Приложение может явно освободить такой дескриптор или неявно освободить его соединение.

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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069931"
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенные дескрипторы
Приложение может явно выделить дескриптор приложения для соединения в любое время, когда оно подключено к базе данных. Если указать этот дескриптор дескриптора как атрибут дескриптора инструкции с помощью **SQLSetStmtAttr**, приложение направляет драйвер на использование этого дескриптора вместо соответствующих неявно выделенных дескрипторов приложений. Приложение не может указывать альтернативные дескрипторы реализации.  
  
 Приложение может связать явно выделенный дескриптор с более чем одной инструкцией. Дескриптор может быть явно выделенным дескриптором, только если приложение действительно подключено к базе данных. Приложение может явно освободить такой дескриптор или неявно освободить его соединение.

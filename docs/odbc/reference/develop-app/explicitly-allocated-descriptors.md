---
title: Явно выделенные дескрипторы Документы Майкрософт
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
ms.openlocfilehash: a9950bc23a1e75606316039e6c2d66f3dba59940
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305695"
---
# <a name="explicitly-allocated-descriptors"></a>Явно выделенные дескрипторы
Приложение может явно распределить дескриптор приложения на соединение в любое время, когда оно подключено к базе данных. Указывая, что дескриптор ручка как атрибут ручки оператора с помощью **S'LSetStmtAttr**, приложение направляет драйверу использовать этот дескриптор вместо соответствующих неявно выделенных дескрипторов приложения. Приложение не может указать альтернативные дескрипторы реализации.  
  
 Приложение может связать явно выделенный дескриптор с более чем одним утверждением. Только тогда, когда приложение действительно подключено к базе данных, дескриптор может быть явно выделенным дескриптором. Приложение может освободить такой дескриптор явно или косвенно, освободив его соединение.

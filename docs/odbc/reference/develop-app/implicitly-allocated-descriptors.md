---
title: Неявно выделенные дескрипторы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 271d479a9d2faa8cd7ab01e02e830b194c4138b2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300134"
---
# <a name="implicitly-allocated-descriptors"></a>Неявно выделенные дескрипторы
При выделении дескриптора инструкции приложение неявно выделяет один набор из четырех дескрипторов. Приложение может получить дескрипторы этих неявно выделенных дескрипторов как атрибуты дескриптора инструкции. Когда приложение освобождает дескриптор инструкции, драйвер освобождает все неявно выделенные дескрипторы на этом дескрипторе.

---
title: Неявно выделенные дескрипторы Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300134"
---
# <a name="implicitly-allocated-descriptors"></a>Неявно выделенные дескрипторы
При выделении ручки оператора приложение неявно выделяет один набор из четырех дескрипторов. Приложение может получить ручки этих неявно выделенных дескрипторов в качестве атрибутов ручки оператора. Когда приложение освобождает ручку оператора, драйвер освобождает все неявно выделенные дескрипторы на этой ручке.

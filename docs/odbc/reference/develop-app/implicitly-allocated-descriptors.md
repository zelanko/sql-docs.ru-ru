---
title: Неявно выделена дескрипторы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19e5608b3d0452bfc4274b51fe4ebe76b908ffe9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="implicitly-allocated-descriptors"></a>Неявно выделенном дескрипторов
Когда выделяется дескриптор инструкции, приложение неявно выделяет один набор из четырех дескрипторов. Приложение может получить дескрипторы они неявно выделена дескрипторов в качестве атрибутов с дескриптором инструкции. Когда приложение освобождает дескриптор инструкции, драйвер освобождаются все дескрипторы неявно выделенном для этого дескриптора.

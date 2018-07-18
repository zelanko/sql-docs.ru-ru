---
title: Неявно выделена дескрипторы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 8d805b110453c5fe0bb5be8c8df067c09ff8146e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913879"
---
# <a name="implicitly-allocated-descriptors"></a>Неявно выделенном дескрипторов
Когда выделяется дескриптор инструкции, приложение неявно выделяет один набор из четырех дескрипторов. Приложение может получить дескрипторы они неявно выделена дескрипторов в качестве атрибутов с дескриптором инструкции. Когда приложение освобождает дескриптор инструкции, драйвер освобождаются все дескрипторы неявно выделенном для этого дескриптора.

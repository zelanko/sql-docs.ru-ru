---
title: "Неявно выделена дескрипторы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0746c31b05302eba9cd1fcf4104336ca139b6938
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="implicitly-allocated-descriptors"></a>Неявно выделенном дескрипторов
Когда выделяется дескриптор инструкции, приложение неявно выделяет один набор из четырех дескрипторов. Приложение может получить дескрипторы они неявно выделена дескрипторов в качестве атрибутов с дескриптором инструкции. Когда приложение освобождает дескриптор инструкции, драйвер освобождаются все дескрипторы неявно выделенном для этого дескриптора.


---
title: 'Шаг 2: Инициализация приложения Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 843155ba6b641ea26717e63af55c8774f963a800
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288270"
---
# <a name="step-2-initialize-the-application"></a>Шаг 2. Инициализация приложения
Вторым шагом является инициализация приложения, как показано на следующей иллюстрации. Именно то, что делается здесь, зависит от приложения.  
  
 ![Инициализация приложения ODBC](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 На данный момент, как обычно, используется **S'LGetInfo,** чтобы обнаружить возможности драйвера. Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
 Все приложения должны выделять ручку оператора с **помощью s'LAllocHandle,** а многие атрибуты оператора, например тип курсора, должны выделять с **помощью S'LSetStmtAttr.** Для получения дополнительной [Allocating a Statement Handle](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) [информации](../../../odbc/reference/develop-app/statement-attributes.md)см.

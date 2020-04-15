---
title: 'Шаг 4b: Получить строку графа (ru) Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31ccbd15ae435165ea007fa9f3c0505c1dcc5aa0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302965"
---
# <a name="step-4b-fetch-the-row-count"></a>Шаг 4б. Выборка числа строк
Следующим шагом является получение количества строк, как показано на следующей иллюстрации.  
  
 ![Выборка количества строк](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Если выписка, выполненная в шаге 3, была **ОБНОВЛЕНИЕ,** **DELETE**, или **заявление INSERT,** приложение получает количество затронутых строк с **S'LRowCount**. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
 Приложение теперь возвращается на шаг 3 для выполнения другого оператора в той же транзакции или переходит к шагу 5, чтобы совершить или откатить транзакцию.

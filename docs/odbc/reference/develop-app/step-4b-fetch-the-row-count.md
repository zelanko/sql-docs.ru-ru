---
title: Шаг 4b. Получение числа строк | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302965"
---
# <a name="step-4b-fetch-the-row-count"></a>Шаг 4б. Выборка числа строк
Следующим шагом является выборка числа строк, как показано на следующем рисунке.  
  
 ![Выборка количества строк](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Если инструкция, выполненная на шаге 3, была инструкцией **Update**, **Delete**или **INSERT** , приложение получает число затронутых строк с помощью **SQLRowCount**. Дополнительные сведения см. [в разделе Определение количества затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Теперь приложение вернется к шагу 3 для выполнения другой инструкции в той же транзакции или переходит к шагу 5 для фиксации или отката транзакции.

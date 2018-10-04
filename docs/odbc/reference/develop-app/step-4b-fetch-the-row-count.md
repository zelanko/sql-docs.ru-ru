---
title: 'Шаг 4б: выборка числа строк | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3091d379bca6c061437e7767fdf6f99d69dc9861
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47763892"
---
# <a name="step-4b-fetch-the-row-count"></a>Шаг 4б. Выборка числа строк
Далее необходимо получить количество строк, как показано на следующем рисунке.  
  
 ![Выборка количества строк](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Если инструкцией, выполненной на шаге 3 была **обновление**, **удалить**, или **вставить** инструкция, приложение получает количество затронутых строк с  **SQLRowCount**. Дополнительные сведения см. в разделе [определение число затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Теперь приложение возвращается к шагу 3, для выполнения другой инструкции в той же транзакции или переходит к шагу 5, чтобы зафиксировать или откатить транзакцию.

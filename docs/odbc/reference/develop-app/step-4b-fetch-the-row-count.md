---
title: Шаг 4б. Выборка числа строк | Документация Майкрософт
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
ms.openlocfilehash: 9455c6589ed93a51e404f3e50d1cb86a0c0c8476
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114160"
---
# <a name="step-4b-fetch-the-row-count"></a>Шаг 4б. Выборка числа строк
Далее необходимо получить количество строк, как показано на следующем рисунке.  
  
 ![Выборка количества строк](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Если инструкцией, выполненной на шаге 3 была **обновление**, **удалить**, или **вставить** инструкция, приложение получает количество затронутых строк с  **SQLRowCount**. Дополнительные сведения см. в разделе [определение число затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Теперь приложение возвращается к шагу 3, для выполнения другой инструкции в той же транзакции или переходит к шагу 5, чтобы зафиксировать или откатить транзакцию.

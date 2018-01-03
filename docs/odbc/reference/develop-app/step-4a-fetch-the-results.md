---
title: "Шаг 4а: извлечь результаты | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application process [ODBC], fetching results
- fetches [ODBC], fetching results
ms.assetid: 77d30142-c774-473c-96fb-b364bb92ac60
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e799fb8290a2ea41093b0b4dcf2234cfc1d51a7e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="step-4a-fetch-the-results"></a>Шаг 4а: получить результаты
Следующий шаг — Выборка результатов, как показано на следующем рисунке.  
  
 ![Выборка результатов в приложении ODBC](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Если был выполнен в «Шаг 3: построение и выполнение инструкции SQL» инструкция **ВЫБЕРИТЕ** инструкция или функция каталога, приложение сначала вызывает **SQLNumResultCols** для определения числа столбцов в результирующем наборе. Этот шаг не является обязательным, если приложение уже знает число результирующий набор столбцов, например, если инструкция SQL жестко запрограммированы в вертикальной или пользовательских приложений.  
  
 После этого приложение получает имя, тип данных, точность и масштаб каждого столбца результирующего набора с **SQLDescribeCol**. Опять же это не требуется для приложений, таких как вертикальной и пользовательских приложений, которые уже известны эти сведения. Приложение передает эту информацию для **SQLBindCol**, который связывает переменную приложения к столбцу в результирующем наборе.  
  
 Теперь приложение вызывает **SQLFetch** получить первую строку данных и помещает данные из этой строки в переменные, привязанные с **SQLBindCol**. Если в строке любой длинных данных, затем вызывается **SQLGetData** для получения данных. Приложение продолжает вызывать **SQLFetch** и **SQLGetData** для получения дополнительных данных. После завершения его выборка данных, он вызывает **SQLCloseCursor** для закрытия курсора.  
  
 Полное описание извлечение результатов см. в разделе [получение результатов (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md) и [получение результатов (Дополнительно)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 Теперь приложение возвращает «Шаг 3: построение и выполнение инструкции SQL» для выполнения другой инструкции в той же транзакции; или переход к «Шаг 5: фиксации транзакции» для фиксации или отката транзакции.

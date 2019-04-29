---
title: Ошибки и пакеты | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97179574407dca56026f9d5216e4978069cffc1e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942987"
---
# <a name="errors-and-batches"></a>Ошибки и пакеты
При возникновении ошибки во время выполнения пакет инструкций SQL, один из следующих четырех результатов возможны. (Каждый возможный результат — это данные, зависящие от источника и даже может зависеть от инструкции, входящие в пакете).  
  
-   Никакие инструкции в пакете не выполнятся.  
  
-   Никакие инструкции в пакете не выполнятся, и выполняется откат транзакции.  
  
-   Все инструкции перед выполнением инструкции ошибка, выполняются.  
  
-   Выполняются все инструкции, за исключением ошибочную инструкцию.  
  
 В первых двух случаях **SQLExecute** и **SQLExecDirect** возвратит SQL_ERROR. В двух последних случаях они могут вернуть значение SQL_SUCCESS_WITH_INFO или SQL_SUCCESS, в зависимости от реализации. Во всех случаях Дополнительные сведения об ошибке можно получить с помощью **SQLGetDiagField**, **SQLGetDiagRec**, или **SQLError**. Однако характер и глубина эти сведения не зависящие от источника данных. Кроме того эти сведения весьма проблематично точно определить инструкцию по ошибке.

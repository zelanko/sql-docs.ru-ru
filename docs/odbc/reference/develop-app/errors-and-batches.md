---
title: "Ошибки и пакеты | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e793309d25bb81eb4b65129f65276ab9ea9091ff
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="errors-and-batches"></a>Ошибки и пакетов
При возникновении ошибки во время выполнения пакета инструкций SQL, один из следующих четырех результатов возможны. (Каждый возможный результат, определяемые источником данных и даже может зависеть от инструкций, включенных в пакет).  
  
-   Никакие инструкции в пакете не выполнятся.  
  
-   Никакие инструкции в пакете не выполнятся и откат транзакции.  
  
-   Выполняются все инструкции перед оператором ошибки.  
  
-   Выполняются все инструкции, за исключением оператора error.  
  
 В первых двух случаях **SQLExecute** и **SQLExecDirect** возвращает SQL_ERROR. В двух последних случаях они могут возвращать значение SQL_SUCCESS_WITH_INFO или SQL_SUCCESS, в зависимости от реализации. Во всех случаях Дополнительные сведения об ошибке можно получить с помощью **SQLGetDiagField**, **SQLGetDiagRec**, или **SQLError**. Однако характер и глубина этой информации является зависящее от источника данных. Кроме того эти сведения вряд ли точно определить инструкцию по ошибке.


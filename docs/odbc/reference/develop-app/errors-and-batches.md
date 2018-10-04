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
ms.openlocfilehash: 61effe29811cc7a8f6e23cbea127b2f757cc7b0c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645942"
---
# <a name="errors-and-batches"></a>Ошибки и пакеты
При возникновении ошибки во время выполнения пакет инструкций SQL, один из следующих четырех результатов возможны. (Каждый возможный результат специфического для источника данных и даже может зависеть от инструкции, входящие в пакете).  
  
-   Никакие инструкции в пакете не выполнятся.  
  
-   Никакие инструкции в пакете не выполнятся, и выполняется откат транзакции.  
  
-   Все инструкции перед выполнением инструкции ошибка, выполняются.  
  
-   Выполняются все инструкции, за исключением ошибочную инструкцию.  
  
 В первых двух случаях **SQLExecute** и **SQLExecDirect** возвратит SQL_ERROR. В двух последних случаях они могут вернуть значение SQL_SUCCESS_WITH_INFO или SQL_SUCCESS, в зависимости от реализации. Во всех случаях Дополнительные сведения об ошибке можно получить с помощью **SQLGetDiagField**, **SQLGetDiagRec**, или **SQLError**. Однако характер и глубина эта информация является специфического для источника данных. Кроме того эти сведения весьма проблематично точно определить инструкцию по ошибке.

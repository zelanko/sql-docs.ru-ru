---
title: Ошибки и пакеты | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 9f9ad11a7f9f0f89e2aa1320b221ce43ac04573e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="errors-and-batches"></a>Ошибки и пакетов
При возникновении ошибки во время выполнения пакета инструкций SQL, один из следующих четырех результатов возможны. (Каждый возможный результат, определяемые источником данных и даже может зависеть от инструкций, включенных в пакет).  
  
-   Никакие инструкции в пакете не выполнятся.  
  
-   Никакие инструкции в пакете не выполнятся и откат транзакции.  
  
-   Выполняются все инструкции перед оператором ошибки.  
  
-   Выполняются все инструкции, за исключением оператора error.  
  
 В первых двух случаях **SQLExecute** и **SQLExecDirect** возвращает SQL_ERROR. В двух последних случаях они могут возвращать значение SQL_SUCCESS_WITH_INFO или SQL_SUCCESS, в зависимости от реализации. Во всех случаях Дополнительные сведения об ошибке можно получить с помощью **SQLGetDiagField**, **SQLGetDiagRec**, или **SQLError**. Однако характер и глубина этой информации является зависящее от источника данных. Кроме того эти сведения вряд ли точно определить инструкцию по ошибке.

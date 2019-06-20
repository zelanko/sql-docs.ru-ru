---
title: Получение сведений о результирующем наборе (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a39a6715a9ba8ab08d846aabb96e5b0665a2aa43
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200292"
---
# <a name="retrieve-result-set-information-odbc"></a>Получение сведений о результирующем наборе (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Получение сведений о результирующем наборе  
  
1.  Вызовите [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) получить количество столбцов в результирующем наборе.  
  
2.  Для каждого столбца в результирующем наборе:  
  
    -   Вызовите [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) для получения сведений о столбце результатов.  
  
     либо  
  
    -   Вызовите [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) чтобы возвратить сведения конкретного дескриптора о столбце результатов.  
  
## <a name="see-also"></a>См. также  
 [Результаты инструкции по обработке &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Определение характеристик результирующего набора &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  

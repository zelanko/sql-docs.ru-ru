---
title: Получить сведения о результирующем наборе (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6d8f1c5640ee0dc8f63b54a2117057b8f334e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099982"
---
# <a name="retrieve-result-set-information-odbc"></a>Получение сведений о результирующем наборе (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Получение сведений о результирующем наборе  
  
1.  Вызовите [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) для получения количества столбцов в результирующем наборе.  
  
2.  Для каждого столбца в результирующем наборе:  
  
    -   Вызовите [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) для получения сведений о столбце результатов.  
  
     либо  
  
    -   Вызовите [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) для получения сведения конкретного дескриптора о столбце результатов.  
  
## <a name="see-also"></a>См. также  
 [Результаты инструкции по обработке &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Определение характеристик результирующего набора &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
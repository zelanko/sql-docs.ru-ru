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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3017f74b12eb18624f8a34e8a1289da18b70c93a
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82712696"
---
# <a name="retrieve-result-set-information-odbc"></a>Получение сведений о результирующем наборе (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Получение сведений о результирующем наборе  
  
1.  Вызовите [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) , чтобы получить количество столбцов в результирующем наборе.  
  
2.  Для каждого столбца в результирующем наборе:  
  
    -   Вызовите [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) , чтобы получить сведения о столбце Result.  
  
     Или  
  
    -   Вызовите [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) , чтобы получить конкретные сведения о дескрипторе столбца результатов.  
  
## <a name="see-also"></a>См. также  
 [Разделы руководства по обработке результатов &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Определение характеристик результирующего набора &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  

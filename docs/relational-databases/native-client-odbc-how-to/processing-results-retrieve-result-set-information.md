---
title: Получение сведений о результирующем наборе (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f2d998dd8b4444298ff67abc8369993d17e26f55
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73780334"
---
# <a name="processing-results---retrieve-result-set-information"></a>Результаты обработки — получение сведений о результирующем наборе
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-get-information-about-a-result-set"></a>Получение сведений о результирующем наборе  
  
1.  Вызовите [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) , чтобы получить количество столбцов в результирующем наборе.  
  
2.  Для каждого столбца в результирующем наборе:  
  
    -   Вызовите [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) , чтобы получить сведения о столбце Result.  
  
     или  
  
    -   Вызовите [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) , чтобы получить конкретные сведения о дескрипторе столбца результатов.  
  
## <a name="see-also"></a>См. также:  
[Обработка результатов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Определение характеристик результирующего набора &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  

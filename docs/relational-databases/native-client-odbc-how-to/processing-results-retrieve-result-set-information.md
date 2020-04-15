---
title: Retrieve Информация о наборе результатов (ODBC) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f1c65841db0fdfd386891cfbd03bdee483ce25f6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300394"
---
# <a name="processing-results---retrieve-result-set-information"></a>Результаты обработки — получение сведений о результирующем наборе
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-get-information-about-a-result-set"></a>Получение сведений о результирующем наборе  
  
1.  Позвоните в [S'LNumResultCols,](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) чтобы получить количество столбцов в наборе результатов.  
  
2.  Для каждого столбца в результирующем наборе:  
  
    -   Позвоните в [S'LDescribeCol,](../../relational-databases/native-client-odbc-api/sqldescribecol.md) чтобы получить информацию о результатах столбца.  
  
     Или  
  
    -   Позвоните [в S'LColAttribute,](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) чтобы получить конкретную информацию о результатах.  
  
## <a name="see-also"></a>См. также:  
[Результаты процесса &#40;&#41;ODBC](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Определение характеристик набора результатов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  

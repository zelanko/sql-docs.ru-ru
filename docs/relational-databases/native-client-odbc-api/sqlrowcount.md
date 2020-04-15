---
title: СЗЛРоутт (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3cfb76dbd1732e32238c484f589d3b4696ff89d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302335"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Если для выполнения инструкции привязаны массивы значений параметров, то функция **SQLRowCount** возвращает значение SQL_ERROR, если любое из значений параметров создаст ошибочное условие при выполнении инструкции. Через аргумент *RowCountPtr* функции значение возвращено не будет.  
  
 Приложение может воспользоваться атрибутом инструкции SQL_ATTR_PARAMS_PROCESSED_PTR для получения количества параметров, обработанных до возникновения ошибки.  
  
 Кроме этого, приложение может использовать массив значений состояния, привязанный с помощью атрибута инструкции SQL_ATTR_PARAM_STATUS_PTR, для получения массива смещений вызвавших ошибку строк параметров. Чтобы выяснить действительное число обработанных строк, приложение может просмотреть этот массив.  
  
 При [!INCLUDE[tsql](../../includes/tsql-md.md)] выполнении оператора INSERT, UPDATE, DELETE или MERGE с оговоркой OUTPUT S'LRowCount не будет возвращать количество затронутых строк до тех пор, пока не будут уничтожены все строки в наборе результатов, порожденных оговоркой OUTPUT. Чтобы поотвелет эти строки, вы звоните в S'LFetch или S'LFetchScroll. S'LResultCols будет возвращаться -1 до тех пор, пока не будут использованы все строки результата. После того, как s'LFetch или S'LFetchScroll возвращается SQL_NO_DATA, приложение должно позвонить в S'LRowCount, чтобы определить количество затронутых строк, прежде чем вызывать S'LMoreResults, чтобы перейти к следующему результату.  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LRowCount](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

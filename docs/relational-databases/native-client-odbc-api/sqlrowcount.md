---
title: SQLRowCount | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 676e2cc86a6b41a1bc778160611a9a967336390f
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785690"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Если для выполнения инструкции привязаны массивы значений параметров, то функция **SQLRowCount** возвращает значение SQL_ERROR, если любое из значений параметров создаст ошибочное условие при выполнении инструкции. Через аргумент *RowCountPtr* функции значение возвращено не будет.  
  
 Приложение может воспользоваться атрибутом инструкции SQL_ATTR_PARAMS_PROCESSED_PTR для получения количества параметров, обработанных до возникновения ошибки.  
  
 Кроме этого, приложение может использовать массив значений состояния, привязанный с помощью атрибута инструкции SQL_ATTR_PARAM_STATUS_PTR, для получения массива смещений вызвавших ошибку строк параметров. Чтобы выяснить действительное число обработанных строк, приложение может просмотреть этот массив.  
  
 При выполнении инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE, DELETE или MERGE с предложением OUTPUT SQLRowCount не будет возвращать количество строк, затронутых до тех пор, пока не будут потреблены все строки результирующего набора, сформированного предложением OUTPUT. Чтобы сконсуме эти строки, вызовите SQLFetch или SQLFetchScroll. Склресултколс возвращает значение-1, пока не будут использованы все строки результатов. После того как SQLFetch или SQLFetchScroll возвращает SQL_NO_DATA, приложение должно вызвать SQLRowCount, чтобы определить число затронутых строк перед вызовом SQLMoreResults для перехода к следующему результату.  
  
## <a name="see-also"></a>См. также статью  
   [функции SQLRowCount](https://go.microsoft.com/fwlink/?LinkId=59367)  
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

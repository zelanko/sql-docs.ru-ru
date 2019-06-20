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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 13a1019d2781ea71f5f1017051f113a985f989be
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014166"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Если для выполнения инструкции привязаны массивы значений параметров, то функция **SQLRowCount** возвращает значение SQL_ERROR, если любое из значений параметров создаст ошибочное условие при выполнении инструкции. Через аргумент *RowCountPtr* функции значение возвращено не будет.  
  
 Приложение может воспользоваться атрибутом инструкции SQL_ATTR_PARAMS_PROCESSED_PTR для получения количества параметров, обработанных до возникновения ошибки.  
  
 Кроме этого, приложение может использовать массив значений состояния, привязанный с помощью атрибута инструкции SQL_ATTR_PARAM_STATUS_PTR, для получения массива смещений вызвавших ошибку строк параметров. Чтобы выяснить действительное число обработанных строк, приложение может просмотреть этот массив.  
  
 Когда [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняется инструкция INSERT, UPDATE, DELETE или MERGE с предложением OUTPUT, то эта функция не возвращает число строк, затронутых пока не обработаны все строки результирующего набора, формируемого предложение OUTPUT. К строкам эти строки осуществляется вызовом SQLFetch или SQLFetchScroll. SQLResultCols возвращает -1, пока не обработаны все результирующие строки. После SQLFetch или SQLFetchScroll вернет значение SQL_NO_DATA, приложение должно вызвать SQLRowCount, чтобы определить количество строк, затронутых перед вызовом SQLMoreResults для перемещения к следующему результату.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLRowCount](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

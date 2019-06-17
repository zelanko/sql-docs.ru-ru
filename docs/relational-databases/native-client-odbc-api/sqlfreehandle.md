---
title: SQLFreeHandle | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9203b6b0708b564645ab5da8cf6788452bc195f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014446"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В режиме с фиксацией вручную вызов функции **SQLFreeHandle** при помощи дескриптора инструкции с открытой транзакцией приводит к откату ожидающих обработки изменений в базе данных. Вызов функции **SQLFreeHandle** применительно к дескриптору инструкции всегда обусловливает закрытие всех открытых курсоров и удаление результатов, ожидающих обработки, что приводит к освобождению всех ресурсов, связанных с дескриптором инструкции.  
  
## <a name="see-also"></a>См. также  
 [SQLFreeHandle, функция](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

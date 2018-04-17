---
title: bcp_done | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_done
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a2cd51a8e4b4bfc79b98fe5218a54258710a3a0e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bcpdone"></a>bcp_done
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Завершает массовое копирование переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполненное с помощью функции [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBINT bcp_done (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
## <a name="returns"></a>Возвращает  
 Число строк окончательно сохраняется после последнего вызова функции [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) или -1 в случае ошибки.  
  
## <a name="remarks"></a>Замечания  
 Вызов функции **bcp_done** после последнего вызова [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) или [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md). Сбой вызова функции **bcp_done** после копирования всех результатов данных в ошибки.  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

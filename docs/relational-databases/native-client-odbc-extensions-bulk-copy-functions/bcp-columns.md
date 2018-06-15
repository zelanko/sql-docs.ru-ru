---
title: bcp_columns | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_columns
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f0509823206c7e2b0062bd3587eb31aeee982369
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32948629"
---
# <a name="bcpcolumns"></a>bcp_columns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Задает общее количество столбцов в файле пользователя, используемых для массового копирования на сервер или с сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md) может использоваться вместо bcp_columns и [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_columns (  
        HDBC hdbc,  
        INT nColumns);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *nColumns*  
 Общее количество столбцов в файле пользователя. Даже если планируется выполнить массовое копирование данных из файла пользователя в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и скопировать все столбцы в файле пользователя не требуется, по-прежнему необходимо задать *nColumns* общего числа столбцов в файле пользователя.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Замечания  
 Эта функция может быть вызван только после [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) был вызван с недопустимым именем файла.  
  
 Эту функцию следует вызывать только в том случае, если планируется использовать формат файла пользователя, отличный от формата по умолчанию. Дополнительные сведения об описании формата файла пользователя по умолчанию см. в разделе **bcp_init**.  
  
 После вызова метода **bcp_columns**, необходимо вызвать [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) для каждого столбца в пользовательском файле, чтобы полностью описать нестандартный формат файла.  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

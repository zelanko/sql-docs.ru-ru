---
title: "bcp_colptr | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_colptr
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ddc9f3139136383e5a4f37b827f6d2c12ecf2c5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="bcpcolptr"></a>bcp_colptr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Устанавливает адрес данных переменных программы для текущей копии в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_colptr (  
        HDBC hdbc,  
        LPCBYTE pData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *pData*  
 Указатель на копируемые данные. Если тип привязанных данных является типом больших значений (например SQLTEXT или SQLIMAGE), *pData* может иметь значение NULL. Значение NULL *pData* указывает значения длинные данные будут отправляться на SQL Server в виде фрагментов с помощью [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Если *pData* имеет значение NULL, а столбец соответствующий привязанному полю не является типом больших значений **bcp_colptr** завершается ошибкой.  
  
 Дополнительные сведения о типах больших значений см. в разделе [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)**.**  
  
 *idxServerCol*  
 Порядковый номер столбца в таблице базы данных, в которую копируются данные. Первый столбец в таблице имеет порядковый номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Замечания  
 **Bcp_colptr** функция позволяет изменять адрес источника данных для конкретного столбца при копировании данных в SQL Server с [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
 Изначально указатель на пользовательские данные устанавливается вызовом **bcp_bind**. Если адрес данных переменных программы изменяется между вызовами **bcp_sendrow**, можно вызвать **bcp_colptr** Чтобы сбросить указатель на данные. При следующем вызове **bcp_sendrow** отправляет данные при помощи вызова **bcp_colptr**.  
  
 Должен быть выполнен отдельный **bcp_colptr** вызова для каждого столбца в таблице, адреса данных которого нужно изменить.  
  
## <a name="see-also"></a>См. также:  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

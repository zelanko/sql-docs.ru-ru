---
description: bcp_colptr
title: bcp_colptr | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_colptr
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74720a7919f9acace77a7f50fd38e7aa89f29794
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499300"
---
# <a name="bcp_colptr"></a>bcp_colptr
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Устанавливает адрес данных переменных программы для текущей копии в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_colptr (  
        HDBC hdbc,  
        LPCBYTE pData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *pData*  
 Указатель на копируемые данные. Если привязанный тип данных имеет тип больших значений (например, SQLTEXT или SQLIMAGE), то параметр *pData* может иметь значение null. ЗНАЧЕНИЕ типа *pData* , указывающее, что данные длинных значений будут отправляться в SQL Server фрагментов с помощью [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Если для *pData* установлено значение null, а столбец, соответствующий привязанному полю, не имеет тип больших значений, **bcp_colptr** завершается ошибкой.  
  
 Дополнительные сведения о типах больших значений см. в разделе [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)**.**  
  
 *idxServerCol*  
 Порядковый номер столбца в таблице базы данных, в которую копируются данные. Первый столбец в таблице имеет порядковый номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращаемое значение  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Комментарии  
 Функция **bcp_colptr** позволяет изменить адрес исходных данных для определенного столбца при копировании данных в SQL Server с помощью [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
 Изначально указатель на пользовательские данные задается вызовом **bcp_bind**. Если адрес данных переменной программы изменяется между вызовами **bcp_sendrow**, можно вызвать **bcp_colptr** , чтобы сбросить указатель на данные. Следующий вызов **bcp_sendrow** отправляет данные, адресованные вызовом **bcp_colptr**.  
  
 Должен существовать отдельный вызов **bcp_colptr** для каждого столбца в таблице, адрес данных которого необходимо изменить.  
  
## <a name="see-also"></a>См. также  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

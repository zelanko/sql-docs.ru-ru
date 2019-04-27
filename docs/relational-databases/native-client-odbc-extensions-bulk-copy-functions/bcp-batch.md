---
title: bcp_batch | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_batch
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6f6899186b328afb8aa7da7c87aaceed10c6637
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62738620"
---
# <a name="bcpbatch"></a>bcp_batch
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Фиксирует все строки, которые ранее были скопированы из переменных программы с использованием массовой операции и переданы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBINT bcp_batch (HDBC  
        hdbc);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
## <a name="returns"></a>Возвращает  
 Количество строк, сохраненных после последнего вызова **bcp_batch**, или -1 в случае ошибки.  
  
## <a name="remarks"></a>Примечания  
 Пакеты массового копирования определяют транзакции. Если приложение использует функции [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) и **bcp_sendrow** для массового копирования строк из переменных программы в таблицы SQL Server, то строки фиксируются только при вызове программой функций **bcp_batch** или [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md).  
  
 Функцию **bcp_batch** можно вызывать один раз для каждых *n* строк или при приостановке поступления данных (например, в телеметрических приложениях). Если приложение не вызывает функцию **bcp_batch** , то строки, для которых выполнено массовое копирование, фиксируются только при вызове функции **bcp_done** .  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

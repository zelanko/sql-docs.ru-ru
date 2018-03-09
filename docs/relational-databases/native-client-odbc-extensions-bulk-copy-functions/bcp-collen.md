---
title: "bcp_collen | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- bcp_collen
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1528b71e05a77034235606f43c9dc455521d79b1
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="bcpcollen"></a>bcp_collen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Устанавливает длину данных в переменной программы для текущего массового копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_collen (  
        HDBC hdbc,  
        DBINT cbData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *cbData*  
 Длина данных в переменной программы, не включая длину признака длины или конца данных. Установка параметра *cbData* в значение SQL_NULL_DATA означает все строки, скопированные на сервер, которые содержат в столбце значение NULL. Установка в значение SQL_VARLEN_DATA означает, что для определения длины скопированных данных используется признак конца строки или другой метод. Если существует как признак длины, так и признак конца, система использует результат с меньшим количеством скопированных данных.  
  
 *idxServerCol*  
 Порядковый номер столбца таблицы, в которую копируются данные. Первый столбец имеет номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Функция **bcp_collen** позволяет изменять для определенного столбца длину данных в переменной программы при копировании данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
 Первоначальная длина данных определяется при вызове функции [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) . Если длина данных изменяется между вызовами функции **bcp_sendrow** и не используется ни одного префикса длины или признака конца, то для сброса длины можно вызвать **bcp_collen** . При следующем вызове функции **bcp_sendrow** используется длина, заданная функцией **bcp_collen**.  
  
 Для каждого столбца таблицы, длину данных которого нужно изменить, необходимо вызвать функцию **bcp_collen** .  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

---
title: bcp_collen | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_collen
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d26efd0d7ebd395dd4453e773bc5bb089ae3792
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73783201"
---
# <a name="bcp_collen"></a>bcp_collen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Устанавливает длину данных в переменной программы для текущего массового копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_collen (  
        HDBC hdbc,  
        DBINT cbData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *cbData*  
 Длина данных в переменной программы, не включая длину признака длины или конца данных. Установка параметра *cbData* в значение SQL_NULL_DATA означает все строки, скопированные на сервер, которые содержат в столбце значение NULL. Установка в значение SQL_VARLEN_DATA означает, что для определения длины скопированных данных используется признак конца строки или другой метод. Если существует как признак длины, так и признак конца, система использует результат с меньшим количеством скопированных данных.  
  
 *idxServerCol*  
 Порядковый номер столбца таблицы, в которую копируются данные. Первый столбец имеет номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Результаты  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Функция **bcp_collen** позволяет изменять для определенного столбца длину данных в переменной программы при копировании данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
 Первоначальная длина данных определяется при вызове функции [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) . Если длина данных изменяется между вызовами функции **bcp_sendrow** и не используется ни одного префикса длины или признака конца, то для сброса длины можно вызвать **bcp_collen** . При следующем вызове функции **bcp_sendrow** используется длина, заданная функцией **bcp_collen**.  
  
 Для каждого столбца таблицы, длину данных которого нужно изменить, необходимо вызвать функцию **bcp_collen** .  
  
## <a name="see-also"></a>См. также:  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

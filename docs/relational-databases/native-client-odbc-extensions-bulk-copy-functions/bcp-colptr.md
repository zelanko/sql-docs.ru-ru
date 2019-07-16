---
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 09dc87f27f1e6cc9dc062addbe97945b47dc7802
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67895707"
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
 Указатель на копируемые данные. Если тип привязанных данных является типом больших значений (например SQLTEXT или SQLIMAGE), *pData* может иметь значение NULL. Значение NULL *pData* означает данные большого будет отправлено в SQL Server в виде фрагментов с помощью [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Если *pData* имеет значение NULL и столбец соответствующий привязанному полю не является типом больших значений **bcp_colptr** завершается ошибкой.  
  
 Дополнительные сведения о типах больших значений см. в разделе [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) **.**  
  
 *idxServerCol*  
 Порядковый номер столбца в таблице базы данных, в которую копируются данные. Первый столбец в таблице имеет порядковый номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 **Bcp_colptr** функция позволяет изменять адрес источника данных для определенного столбца, при копировании данных в SQL Server с [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
 Изначально указатель на пользовательские данные устанавливается вызовом **bcp_bind**. Если адрес данных переменных программы изменяется между вызовами **bcp_sendrow**, можно вызвать **bcp_colptr** Чтобы сбросить указатель на данные. Следующий вызов **bcp_sendrow** отправляет данные путем вызова **bcp_colptr**.  
  
 Должен быть отдельный **bcp_colptr** вызова для каждого столбца в таблице, адреса данных которого нужно изменить.  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

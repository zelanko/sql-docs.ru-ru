---
title: bcp_sendrow | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5898c55baa1cb3447c97fd42e8435217c3a11325
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666282"
---
# <a name="bcpsendrow"></a>bcp_sendrow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Отправляет строку данных из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 **Bcp_sendrow** функция формирует строку из переменных программы и отправляет ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Перед вызовом **bcp_sendrow**, необходимо вызвать функцию [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) чтобы указать переменные программы, содержащие данные строки.  
  
 Если **bcp_bind** вызывается с указанием типа данных long, переменной длины, например, *eDataType* параметр SQLTEXT и отличный от NULL *pData* параметр, **bcp_sendrow** отправляет значения типа данных, так же, как для любого другого типа данных. Если, однако **bcp_bind** имеет значение NULL *pData* параметр, **bcp_sendrow** возвращает управление приложению сразу после отправляются все указанные столбцы с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Затем приложение может вызвать [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) многократно, чтобы отправлять данные long и variable-length [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], данных за раз. Дополнительные сведения см. в разделе [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Когда **bcp_sendrow** используется для массового копирования строк из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, строки фиксируются только в том случае, когда пользователь вызывает [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) или [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) . Пользователь может вызывать функцию **bcp_batch** один раз для каждой из *n* строк или во время перерыва между периодами поступления данных. Если функция **bcp_batch** никогда не вызывается, то строки фиксируются при вызове функции **bcp_done** .  
  
 Сведения о важных изменениях в массовом копировании, начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], см. в разделе [выполнение операций массового копирования &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

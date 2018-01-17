---
title: "bcp_sendrow | Документы Microsoft"
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
apiname: bcp_sendrow
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e332dbcf96d58b867029a3a5ec4f7be950b1992d
ms.sourcegitcommit: 779f3398e4e3f4c626d81ae8cedad153bee69540
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2018
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
  
## <a name="remarks"></a>Remarks  
 **Bcp_sendrow** функция формирует строку из переменных программы и отправляет ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Перед вызовом метода **bcp_sendrow**, необходимо вызвать функцию [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) для указания переменных программы, содержащие данные строки.  
  
 Если **bcp_bind** вызывается с указанием типа данных long, переменной длины, например, *eDataType* параметр SQLTEXT и НЕНУЛЕВОЙ *pData* параметр, **bcp_sendrow** отправляет значения типа данных, как и в случае любой другой тип данных. Если, однако **bcp_bind** имеет значение NULL *pData* параметр **bcp_sendrow** возвращает управление приложению сразу после отправляются все указанные столбцы с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Затем приложение может вызвать [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) многократно, для отправки данных long, переменной длины в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одному фрагменту данных за раз. Дополнительные сведения см. в разделе [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Когда **bcp_sendrow** используется для массового копирования строк из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, строки фиксируются только в том случае, когда пользователь вызывает [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) или [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) . Пользователь может выбрать для вызова **bcp_batch** после каждого  *n*  строк или при наличии время перерыва между периодами поступления данных. Если функция **bcp_batch** никогда не вызывается, то строки фиксируются при вызове функции **bcp_done** .  
  
 Сведения о важных изменениях в массовом копировании, начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], в разделе [выполнение операций массового копирования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

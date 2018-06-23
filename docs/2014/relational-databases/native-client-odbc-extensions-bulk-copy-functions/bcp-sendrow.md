---
title: bcp_sendrow | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97229063d5ce78ebae1293eb85b05ee8765fc4c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095442"
---
# <a name="bcpsendrow"></a>bcp_sendrow
  Отправляет строку данных из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 **Bcp_sendrow** функция формирует строку из переменных программы и отправляет ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Перед вызовом метода **bcp_sendrow**, необходимо вызвать функцию [bcp_bind](bcp-bind.md) для указания переменных программы, содержащие данные строки.  
  
 Если функция **bcp_bind** вызывается с указанием типа данных большого объема переменной длины, например параметра *eDataType* SQLTEXT и параметра *pData* , отличного от значения NULL, функция **bcp_sendrow** отправляет все данные значения, также как и для любого другого типа данных. Если, однако **bcp_bind** имеет значение NULL *pData* параметр **bcp_sendrow** возвращает управление приложению сразу после отправляются все указанные столбцы с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Затем приложение может вызвать [bcp_moretext](bcp-moretext.md) многократно, для отправки данных long, переменной длины в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одному фрагменту данных за раз. Дополнительные сведения см. в разделе [bcp_moretext](bcp-moretext.md).  
  
 Когда **bcp_sendrow** используется для массового копирования строк из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, строки фиксируются только в том случае, когда пользователь вызывает [bcp_batch](bcp-batch.md) или [bcp_done](bcp-done.md) . Пользователь может вызывать функцию **bcp_batch** один раз для каждой из *n* строк или во время перерыва между периодами поступления данных. Если функция **bcp_batch** никогда не вызывается, то строки фиксируются при вызове функции **bcp_done** .  
  
 Сведения о важных изменениях в массовом копировании, начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], в разделе [выполнение операций массового копирования &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
---
title: bcp_sendrow | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2810dd25a14f35ed275a7d1117fc21d7946cc90e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423543"
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
  
 Перед вызовом **bcp_sendrow**, необходимо вызвать функцию [bcp_bind](bcp-bind.md) чтобы указать переменные программы, содержащие данные строки.  
  
 Если функция **bcp_bind** вызывается с указанием типа данных большого объема переменной длины, например параметра *eDataType* SQLTEXT и параметра *pData* , отличного от значения NULL, функция **bcp_sendrow** отправляет все данные значения, также как и для любого другого типа данных. Если, однако **bcp_bind** имеет значение NULL *pData* параметр, **bcp_sendrow** возвращает управление приложению сразу после отправляются все указанные столбцы с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Затем приложение может вызвать [bcp_moretext](bcp-moretext.md) многократно, чтобы отправлять данные long и variable-length [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], данных за раз. Дополнительные сведения см. в разделе [bcp_moretext](bcp-moretext.md).  
  
 Когда **bcp_sendrow** используется для массового копирования строк из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, строки фиксируются только в том случае, когда пользователь вызывает [bcp_batch](bcp-batch.md) или [bcp_done](bcp-done.md) . Пользователь может вызывать функцию **bcp_batch** один раз для каждой из *n* строк или во время перерыва между периодами поступления данных. Если функция **bcp_batch** никогда не вызывается, то строки фиксируются при вызове функции **bcp_done** .  
  
 Сведения о важных изменениях в массовом копировании, начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], см. в разделе [выполнение операций массового копирования &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

---
title: bcp_sendrow | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e8ef7aa7a4354f5a3fbc334504512b2ee8d131b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62688833"
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
 Функция **bcp_sendrow** формирует строку из переменных программы и отправляет ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Перед вызовом функции **bcp_sendrow**необходимо вызвать функцию [bcp_bind](bcp-bind.md) , чтобы указать переменные программы, содержащие данные строки.  
  
 Если функция **bcp_bind** вызывается с указанием типа данных большого объема переменной длины, например параметра *eDataType* SQLTEXT и параметра *pData* , отличного от значения NULL, функция **bcp_sendrow** отправляет все данные значения, также как и для любого другого типа данных. Однако, если в функции **bcp_bind** параметр *pData* имеет значение NULL, функция **bcp_sendrow** возвращает управление приложению сразу после того, как все указанные столбцы с данными отправляются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Затем приложение может повторно вызывать функцию [bcp_moretext](bcp-moretext.md) , чтобы отправлять данные большого объема переменной длины в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]по одному фрагменту данных за раз. Дополнительные сведения см. в разделе [bcp_moretext](bcp-moretext.md).  
  
 Если функция **bcp_sendrow** используется для массового копирования строк из переменных программы в таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , строки фиксируются только при вызове пользователем функции [bcp_batch](bcp-batch.md) или [bcp_done](bcp-done.md). Пользователь может вызывать функцию **bcp_batch** один раз для каждой из *n* строк или во время перерыва между периодами поступления данных. Если функция **bcp_batch** никогда не вызывается, то строки фиксируются при вызове функции **bcp_done** .  
  
 Сведения о важных изменениях в массовом копировании, начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], см. в разделе [выполнение операций массового копирования &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

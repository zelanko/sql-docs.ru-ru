---
title: bcp_done | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ca26e8e8f3bdb17afe9908b99bfe5cf09ff3b563
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701983"
---
# <a name="bcp_done"></a>bcp_done
  Завершает массовое копирование переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполненное с помощью функции [bcp_sendrow](bcp-sendrow.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
## <a name="returns"></a>Возвращаемое значение  
 Число строк окончательно сохраняется после последнего вызова функции [bcp_batch](bcp-batch.md) или -1 в случае ошибки.  
  
## <a name="remarks"></a>Remarks  
 Вызов функции **bcp_done** после последнего вызова [bcp_sendrow](bcp-sendrow.md) или [bcp_moretext](bcp-moretext.md). Сбой вызова функции **bcp_done** после копирования всех результатов данных в ошибки.  
  
## <a name="see-also"></a>См. также  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

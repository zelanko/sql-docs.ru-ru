---
title: bcp_done | Документы Microsoft
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
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 56c1d20d56d95263e93e33a45f712447b749b1be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195380"
---
# <a name="bcpdone"></a>bcp_done
  Завершает массовое копирование переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполненное с помощью функции [bcp_sendrow](bcp-sendrow.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
## <a name="returns"></a>Возвращает  
 Число строк окончательно сохраняется после последнего вызова функции [bcp_batch](bcp-batch.md) или -1 в случае ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызов функции **bcp_done** после последнего вызова [bcp_sendrow](bcp-sendrow.md) или [bcp_moretext](bcp-moretext.md). Сбой вызова функции **bcp_done** после копирования всех результатов данных в ошибки.  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
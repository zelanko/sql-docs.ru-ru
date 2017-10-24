---
title: "Свойство ConnectionTimeout (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d00956df35fc6b3f5d6d864ea72d9efdea69fe56
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connectiontimeout-property-ado"></a>Свойство ConnectionTimeout (ADO)
Указывает время ожидания при установлении подключения, по истечении которого попытка завершается и создается ошибка.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, которое указывает, в секундах время ожидания открытия соединения. По умолчанию — 15.  
  
## <a name="remarks"></a>Замечания  
 Используйте **ConnectionTimeout** свойство [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, если задержки от использования сетевой трафик или тяжелой сервера необходимо отказаться от попытки подключения. Если время из **ConnectionTimeout** задания свойств истекает до открытия соединения, возникает ошибка и ADO отменяет попытку выполнения. Если это свойство равно нулю, ADO будет ждать неограниченное время открытия подключения. Убедитесь, что поставщик, который вы пишете код поддерживает **ConnectionTimeout** функциональные возможности.  
  
 **ConnectionTimeout** свойство является чтение и запись, когда подключение закрыто, только для чтения при открытом.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [ConnectionString, ConnectionTimeout и пример свойства состояния (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout и пример свойства состояния (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Свойство CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)


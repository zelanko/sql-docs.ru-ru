---
title: Свойство ConnectionTimeout (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07d39c9b4ad20a9cfe0c9c906c9f64a12f2bf0d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connectiontimeout-property-ado"></a>Свойство ConnectionTimeout (ADO)
Указывает время ожидания при установлении подключения, по истечении которого попытка завершается и создается ошибка.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, которое указывает, в секундах время ожидания открытия соединения. По умолчанию — 15.  
  
## <a name="remarks"></a>Замечания  
 Используйте **ConnectionTimeout** свойство [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, если задержки от использования сетевой трафик или тяжелой сервера необходимо отказаться от попытки подключения. Если время из **ConnectionTimeout** задания свойств истекает до открытия соединения, возникает ошибка и ADO отменяет попытку выполнения. Если это свойство равно нулю, ADO будет ждать неограниченное время открытия подключения. Убедитесь, что поставщик, который вы пишете код поддерживает **ConnectionTimeout** функциональные возможности.  
  
 **ConnectionTimeout** свойство является чтение и запись, когда подключение закрыто, только для чтения при открытом.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [ConnectionString, ConnectionTimeout и пример свойства состояния (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout и пример свойства состояния (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Свойство CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)

---
title: Свойство ConnectionTimeout (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 594c96d73302b907f5bc9b2167f69c8b33047aab
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698632"
---
# <a name="connectiontimeout-property-ado"></a>Свойство ConnectionTimeout (ADO)
Указывает время ожидания при установлении соединения перед завершается и генерируется ошибка.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Long** значение, которое указывает, в секундах время ожидания открытия соединения. Значение по умолчанию — 15.  
  
## <a name="remarks"></a>Примечания  
 Используйте **ConnectionTimeout** свойство [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, если задержки от использования сервера сетевой трафик или большим числом операций необходимо отказаться от попытки подключения. Если время из **ConnectionTimeout** задания свойств, по истечении перед открытием подключения, возникает ошибка и ADO не отменит попытку. Если свойство задано равным нулю, ADO будет ждать неограниченное время открытия подключения. Убедитесь, что поставщик, к которому при написании кода поддерживает **ConnectionTimeout** функциональные возможности.  
  
 **ConnectionTimeout** свойство доступно чтения и записи, когда подключение будет закрытым или только для чтения, когда он открыт.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства состояния (Visual Basic), ConnectionString и ConnectionTimeout](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout и пример свойства состояния (Visual C++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Свойство CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)

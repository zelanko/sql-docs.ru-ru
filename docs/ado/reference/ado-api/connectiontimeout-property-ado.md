---
description: Свойство ConnectionTimeout (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c117974f9335ef3aa939f742781f3f381ab6cbd2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444446"
---
# <a name="connectiontimeout-property-ado"></a>Свойство ConnectionTimeout (ADO)
Указывает время ожидания при установлении соединения перед завершением попытки и генерацией ошибки.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , указывающее время ожидания открытия соединения (в секундах). Значение по умолчанию — 15.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ConnectionTimeout** для объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) , если задержка сетевого трафика или интенсивного использования сервера потребовала для отмены попытки подключения. Если время, заданное свойством **ConnectionTimeout** , проходит до открытия соединения, возникает ошибка, и ADO отменяет попытку. Если присвоить свойству значение 0, то при открытии соединения ADO будет ждать неограниченно долго. Убедитесь, что поставщик, в котором пишется код, поддерживает функцию **ConnectionTimeout** .  
  
 Свойство **ConnectionTimeout** доступно для чтения и записи, когда соединение закрывается и доступно только для чтения, когда оно открыто.  
  
## <a name="applies-to"></a>Применение  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual c++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Свойство CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)

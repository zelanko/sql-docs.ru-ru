---
description: Свойство ConnectionTimeout (ADO)
title: Свойство ConnectionTimeout (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: bd8fd11c017583ef49981021688210245589e971
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974745"
---
# <a name="connectiontimeout-property-ado"></a>Свойство ConnectionTimeout (ADO)
Указывает время ожидания при установлении соединения перед завершением попытки и генерацией ошибки.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , указывающее время ожидания открытия соединения (в секундах). Значение по умолчанию — 15.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ConnectionTimeout** для объекта [соединения](./connection-object-ado.md) , если задержка сетевого трафика или интенсивного использования сервера потребовала для отмены попытки подключения. Если время, заданное свойством **ConnectionTimeout** , проходит до открытия соединения, возникает ошибка, и ADO отменяет попытку. Если присвоить свойству значение 0, то при открытии соединения ADO будет ждать неограниченно долго. Убедитесь, что поставщик, в котором пишется код, поддерживает функцию **ConnectionTimeout** .  
  
 Свойство **ConnectionTimeout** доступно для чтения и записи, когда соединение закрывается и доступно только для чтения, когда оно открыто.  
  
## <a name="applies-to"></a>Применение  
 [Объект Connection (ADO)](./connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual Basic)](./connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual c++)](./connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Свойство CommandTimeout (ADO)](./commandtimeout-property-ado.md)
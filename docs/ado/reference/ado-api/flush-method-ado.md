---
title: Метод Flush (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66deae3833a738075259928855881f87b64ef0dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636072"
---
# <a name="flush-method-ado"></a>Метод Flush (ADO)
Заставляет содержимое [Stream](../../../ado/reference/ado-api/stream-object-ado.md) остающихся в буфере ADO к базовому объекту с помощью которого **Stream** связан.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Примечания  
 Этот метод можно использовать для отправки содержимого буфера потока к базовому объекту: например, узел или файл, представленный URL-адрес, который является источником **Stream** объекта. Этот метод должен быть вызван, если вы хотите убедиться, что все изменения, внесенные в содержимое **Stream** были записаны. Тем не менее, с помощью ADO необязательно обычно для вызова **Flush**, как ADO постоянно очищает его буфер, насколько это возможно в фоновом режиме. Изменения в содержимое **Stream** , производятся автоматически не кэшируются до **Flush** вызывается.  
  
 Закрытие **Stream** с [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод сбрасывает содержимое **Stream** автоматически; существует это не нужно явно вызывать **Flush**непосредственно перед **закрыть**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

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
ms.openlocfilehash: f3d9ab76d2f2ed1a6f5dbeaf58be7d2f919acd3a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932546"
---
# <a name="flush-method-ado"></a>Метод Flush (ADO)
Принудительно применяет содержимое [потока](../../../ado/reference/ado-api/stream-object-ado.md) , остающегося в буфере ADO, к базовому объекту, с которым связан **поток** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Remarks  
 Этот метод можно использовать для отправки содержимого буфера потока в базовый объект: например, узел или файл, представленный URL-адресом, который является источником объекта **потока** . Этот метод следует вызывать, если необходимо обеспечить запись всех изменений, внесенных в содержимое **потока** . Однако при использовании ADO обычно не требуется вызывать **Сброс**, так как ADO постоянно очищает свой буфер в фоновом режиме. Изменения содержимого **потока** вносятся автоматически, а не кэшируются до вызова метода **flush** .  
  
 При закрытии **потока** с помощью метода [Close](../../../ado/reference/ado-api/close-method-ado.md) содержимое **потока** автоматически очищается. нет необходимости явно вызывать метод **flush** непосредственно перед **закрытием**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

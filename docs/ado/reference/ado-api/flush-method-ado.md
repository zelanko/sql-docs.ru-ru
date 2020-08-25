---
description: Метод Flush (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 532a6bf973960e5c6a0a7d6f44ff8e0a2c2d1d09
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775143"
---
# <a name="flush-method-ado"></a>Метод Flush (ADO)
Принудительно применяет содержимое [потока](./stream-object-ado.md) , остающегося в буфере ADO, к базовому объекту, с которым связан **поток** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Remarks  
 Этот метод можно использовать для отправки содержимого буфера потока в базовый объект: например, узел или файл, представленный URL-адресом, который является источником объекта **потока** . Этот метод следует вызывать, если необходимо обеспечить запись всех изменений, внесенных в содержимое **потока** . Однако при использовании ADO обычно не требуется вызывать **Сброс**, так как ADO постоянно очищает свой буфер в фоновом режиме. Изменения содержимого **потока** вносятся автоматически, а не кэшируются до вызова метода **flush** .  
  
 При закрытии **потока** с помощью метода [Close](./close-method-ado.md) содержимое **потока** автоматически очищается. нет необходимости явно вызывать метод **flush** непосредственно перед **закрытием**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)
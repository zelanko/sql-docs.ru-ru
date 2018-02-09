---
title: "Flush-метод (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 94a5e1ced6f0b302253298dcbfb9cd345b9f5bfe
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="flush-method-ado"></a>Flush-метод (ADO)
Заставляет содержимое [поток](../../../ado/reference/ado-api/stream-object-ado.md) оставшиеся в буфере ADO для базового объекта, с которым **поток** связан.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Remarks  
 Этот метод можно использовать для отправки содержимого буфера потока к базовому объекту: например, узел или файл, представленный URL-адрес, который является источником **поток** объекта. Этот метод должен вызываться, если вы хотите убедиться, что все изменения, внесенные в содержимое **поток** были записаны. Однако при использовании ADO необязательно обычно для вызова **Flush**, как ADO постоянно записывает свой буфер, насколько возможно в фоновом режиме. Изменения содержимого **поток** производится автоматически, не кэшируются до **Flush** вызывается.  
  
 Закрытие **поток** с [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод сбрасывает содержимое **поток** автоматически; существует это не требуется явно вызывать **Flush**непосредственно перед **закрыть**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

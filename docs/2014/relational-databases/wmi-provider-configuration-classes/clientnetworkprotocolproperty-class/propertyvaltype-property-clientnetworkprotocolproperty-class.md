---
title: Свойство PropertyValType (класс ClientNetworkProtocolProperty) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PropertyValType Property (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: 624b9bdd-ed93-4140-bd4e-00d714a2558c
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd4238a43c5bc8a31e33bae9993c52b05e9e750b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096360"
---
# <a name="propertyvaltype-property-clientnetworkprotocolproperty-class"></a>Свойство PropertyValType (класс ClientNetworkProtocolProperty)
  Возвращает тип данных значения, хранящегося в свойстве, на которое ссылается значение свойства [PropertyIdx (класс ClientNetworkProtocolProperty)](clientnetworkprotocolproperty-class.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocolProperty](clientnetworkprotocolproperty-class.md) , который представляет атрибут сетевого протокола, используемого [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, представляющее тип данных для значения свойства.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
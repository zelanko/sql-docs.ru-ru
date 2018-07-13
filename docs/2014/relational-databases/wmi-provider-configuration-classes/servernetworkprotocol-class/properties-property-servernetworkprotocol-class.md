---
title: Свойство Properties (класс ServerNetworkProtocol) | Документация Майкрософт
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
- Properties Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 6c971bfc-c277-4c1e-a06e-146dcc34e759
caps.latest.revision: 29
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cf3384908284cb25a59c35451706b0e3e535e345
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157875"
---
# <a name="properties-property-servernetworkprotocol-class"></a>Свойство Properties (класс ServerNetworkProtocol)
  Возвращает свойства, связанные с сетевым протоколом сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ServerNetworkProtocol](servernetworkprotocol-class.md) , который представляет сетевой протокол, используемый экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив объектов класса [ServerNetworkProtocolIPAdress](../servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) , представляющих свойства, поддерживаемые сетевым протоколом сервера.  
  
## <a name="remarks"></a>Примечания  
  

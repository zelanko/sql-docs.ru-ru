---
title: Свойство NumberOfFlags (класс ClientNetworkProtocol) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- NumberOfFlags Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- NumberOfFlags property
ms.assetid: 7a656644-2154-419f-9787-99877f597770
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6be2a4a4e85b3d92cb44db8783dfa7c12e595f87
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057104"
---
# <a name="numberofflags-property-clientnetworkprotocol-class"></a>Свойство NumberOfFlags (класс ClientNetworkProtocol)
  Получает число параметров флага, необходимых сетевому протоколу клиента, определяемое [Setordervalue (класс ClientNetworkProtocol)](clientnetworkprotocol-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.NumberofFlags [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ClientNetworkProtocol](clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `Uint32`, определяющее число параметров флага, необходимых сетевому протоколу клиента, на который ссылается свойство `OrderValue`.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](http://technet.microsoft.com/library/ms181035.aspx)  
  
  

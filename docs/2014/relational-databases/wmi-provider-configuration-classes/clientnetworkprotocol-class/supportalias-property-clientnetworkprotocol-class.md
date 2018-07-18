---
title: Свойство SupportAlias (класс ClientNetworkProtocol) | Документация Майкрософт
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
- SupportAlias Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: bd18c837ca94878887bdf30fc0412dddff59cb83
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327554"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>Свойство SupportAlias (класс ClientNetworkProtocol)
  Возвращает логическое свойство, указывающее, является ли текущий сетевой протокол, заданный по [Setordervalue (класс ClientNetworkProtocol)](clientnetworkprotocol-class.md) поддерживает псевдонимы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ClientNetworkProtocol](clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, которое указывает, поддерживает ли псевдонимы сетевой протокол клиента:  
  
 если значение равно True, сетевой протокол клиента поддерживает псевдонимы;  
  
 если значение равно False, сетевой протокол клиента не поддерживает псевдонимы.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](http://technet.microsoft.com/library/ms181035.aspx)  
  
  

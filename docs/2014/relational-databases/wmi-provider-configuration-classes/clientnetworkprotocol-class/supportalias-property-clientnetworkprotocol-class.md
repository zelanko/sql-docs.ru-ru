---
title: Свойство SupportAlias (класс класс clientnetworkprotocol) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d28ec166f8954b874f98b7f9f441280ab9064f1f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62826760"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>Свойство SupportAlias (класс ClientNetworkProtocol)
  Возвращает логическое свойство, указывающее, поддерживает ли текущий сетевой протокол, заданный [методом SetOrderValue (класс класс clientnetworkprotocol)](clientnetworkprotocol-class.md) , псевдонимы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 A [класса ClientNetworkProtocol](clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, которое указывает, поддерживает ли псевдонимы сетевой протокол клиента:  
  
 если значение равно True, сетевой протокол клиента поддерживает псевдонимы;  
  
 если значение равно False, сетевой протокол клиента не поддерживает псевдонимы.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  

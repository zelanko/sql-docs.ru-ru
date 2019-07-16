---
title: Свойство SupportAlias (класс ClientNetworkProtocol) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SupportAlias Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4cd3ba42974c65591f7920d5df8d7dd8a937d352
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68040833"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>Свойство SupportAlias (класс ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает логическое свойство, указывающее, является ли текущий сетевой протокол, заданный по [Setordervalue (класс ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md) поддерживает псевдонимы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SupportAlias [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, которое указывает, поддерживает ли псевдонимы сетевой протокол клиента:  
  
 если значение равно True, сетевой протокол клиента поддерживает псевдонимы;  
  
 если значение равно False, сетевой протокол клиента не поддерживает псевдонимы.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  

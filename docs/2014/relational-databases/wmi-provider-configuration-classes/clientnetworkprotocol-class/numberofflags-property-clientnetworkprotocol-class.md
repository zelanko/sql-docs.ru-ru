---
title: Свойство NumberOfFlags (класс класс clientnetworkprotocol) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
ms.openlocfilehash: 9a47f6e17a85fdf9cec169a611b9fe205ba02543
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63192042"
---
# <a name="numberofflags-property-clientnetworkprotocol-class"></a>Свойство NumberOfFlags (класс ClientNetworkProtocol)
  Возвращает число параметров флага, необходимых сетевому протоколу клиента, заданному [методом SetOrderValue (класс класс clientnetworkprotocol)](clientnetworkprotocol-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.NumberofFlags [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 A [класса ClientNetworkProtocol](clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `Uint32`, определяющее число параметров флага, необходимых сетевому протоколу клиента, на который ссылается свойство `OrderValue`.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  

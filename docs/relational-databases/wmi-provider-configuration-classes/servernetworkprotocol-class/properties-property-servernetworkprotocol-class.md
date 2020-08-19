---
description: Свойство Properties (класс ServerNetworkProtocol)
title: Свойство Properties (класс servernetworkprotocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Properties Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Properties property
ms.assetid: 6c971bfc-c277-4c1e-a06e-146dcc34e759
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bc587824aa56dad677e679e24e23062a3a7d7fdb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446220"
---
# <a name="properties-property-servernetworkprotocol-class"></a>Свойство Properties (класс ServerNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает свойства, связанные с сетевым протоколом сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Properties [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ServerNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) , который представляет сетевой протокол, используемый экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив объектов класса [ServerNetworkProtocolIPAdress](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) , представляющих свойства, поддерживаемые сетевым протоколом сервера.  
  
## <a name="remarks"></a>Remarks  
  

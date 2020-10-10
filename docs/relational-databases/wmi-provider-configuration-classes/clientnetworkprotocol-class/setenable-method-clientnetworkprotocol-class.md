---
description: Метод SetEnable (класс ClientNetworkProtocol)
title: Метод SetEnable (класс clientnetworkprotocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetEnable Method (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetEnable method
ms.assetid: a66c756a-1311-4f4a-8088-818f8ed90056
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dcc745710132ea85b7027152900b7d693df37aab
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91889080"
---
# <a name="setenable-method-clientnetworkprotocol-class"></a>Метод SetEnable (класс ClientNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Включает сетевой протокол клиента, указанный в параметре [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetEnableMethod()  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Настройка сетевых протоколов клиента и сетевых библиотек](../../../database-engine/configure-windows/configure-client-protocols.md)  
  

---
description: Класс CInstance — метод SetDefaults
title: Метод SetDefaults (CInstance)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (CInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 99771d12be4c10d8d4b823ceb788e9722d417fca
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91890984"
---
# <a name="cinstance-class---setdefaults-method"></a>Класс CInstance — метод SetDefaults
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Задает все значения по умолчанию для экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиента с возможностью перезаписи существующих данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса CInstance](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) , представляющий экземпляр клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Description|  
|---------------|-----------------|  
|*овервритеалл*|Логическое значение, указывающее, следует ли перезаписывать существующие значения в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиента: **true** для перезаписи существующих данных, или **false** , если существующие данные не будут перезаписаны.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)  
  

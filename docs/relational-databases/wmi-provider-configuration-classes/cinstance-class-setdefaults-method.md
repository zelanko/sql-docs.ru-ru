---
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d75a202b368df339b97a4a9588ad3ac073429c6e
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73659643"
---
# <a name="cinstance-class---setdefaults-method"></a>Класс CInstance — метод SetDefaults
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Задает все значения по умолчанию для экземпляра клиента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с параметром перезаписи существующих данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса CInstance](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) , представляющий экземпляр клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*овервритеалл*|Логическое значение, указывающее, следует ли перезаписывать существующие значения в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиента: **true** для перезаписи существующих данных или **значение false** , если существующие данные не будут перезаписаны.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  

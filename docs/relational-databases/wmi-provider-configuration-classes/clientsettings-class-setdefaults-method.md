---
title: Метод SetDefaults (класс ClientSettings) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (ClientSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b2b079d70a8fb70a2b28c139a862f0689bd33d5f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072489"
---
# <a name="clientsettings-class---setdefaults-method"></a>Класс ClientSettings — метод SetDefaults
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Задает все значения по умолчанию для экземпляра клиента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с параметром перезаписи существующих данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект **ClientSettings** , представляющий экземпляр клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*OverwriteAll*|Логическое значение, указывающее, следует ли перезаписывать существующие значения в экземпляре клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **true** для перезаписи, **false** для сохранения существующих значений.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  

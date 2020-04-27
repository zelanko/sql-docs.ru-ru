---
title: Метод SetDefaults (класс ClientSettings) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ClientSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ce71d591dc8f72e6826f7bcd96628fb1898fd7bd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63242944"
---
# <a name="setdefaults-method-clientsettings-class"></a>Метод SetDefaults (класс ClientSettings)
  Задает все значения по умолчанию для экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиента с возможностью перезаписи существующих данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект `ClientSettings`, представляющий экземпляр клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*овервритеалл*|Логическое значение, указывающее, следует ли перезаписывать существующие значения в экземпляре клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : `true` для перезаписи, `false` для сохранения существующих значений.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  

---
title: "Свойство PropertyIndex (класс SqlServiceAdvancedProperty) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PropertyIndex Property (SqlServiceAdvancedProperty Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: PropertyIndex property
ms.assetid: b18b45a2-e187-44f5-a8c9-26fd9828b6c6
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d3bd3277fb0c045ace4a92ff420211adc01f41b7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="propertyindex-property-sqlserviceadvancedproperty-class"></a>Свойство PropertyIndex (класс SqlServiceAdvancedProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Возвращает или задает индекс свойства, указывающее положение дополнительного свойства в массиве дополнительных свойств, которые принадлежат указанной службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.PropertyIndex [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Объект **uint32** значение, определяющее положение дополнительного свойства в массиве дополнительных свойств, к которой принадлежит указанной службы.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

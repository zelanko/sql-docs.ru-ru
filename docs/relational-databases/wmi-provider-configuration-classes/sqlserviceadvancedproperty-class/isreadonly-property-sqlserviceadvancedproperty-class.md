---
title: "Свойство IsReadOnly (класс SqlServiceAdvancedProperty) | Документы Microsoft"
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
apiname: IsReadOnly Property (SqlServiceAdvancedProperty Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: IsReadOnly property
ms.assetid: 9672e70f-1d8c-4133-ac73-3b5733a1c4ee
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33cf2d1415354406e50037da506cc05fb11e7bae
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="isreadonly-property-sqlserviceadvancedproperty-class"></a>Свойство IsReadOnly (класс SqlServiceAdvancedProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Возвращает или задает логическое свойство, указывающее, является ли дополнительное свойство только для чтения или нет.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.IsReadOnly [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, определяющее, предназначено ли дополнительное свойство только для чтения: **true** , если да; **false** , если дополнительное свойство можно модифицировать.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

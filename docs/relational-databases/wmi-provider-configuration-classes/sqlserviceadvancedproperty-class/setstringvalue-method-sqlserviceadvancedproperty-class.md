---
title: Метод SetStringValue (класс SqlServiceAdvancedProperty) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SetStringValue Method (SqlServiceAdvancedProperty Class )
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStringValue method
ms.assetid: a02d05f6-1072-4709-9ecc-e23e51c8c898
caps.latest.revision: 15
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7660711ce50b10a705a9b3f2386530dab9297bf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setstringvalue-method-sqlserviceadvancedproperty-class-"></a>Метод SetStringValue (класс SqlServiceAdvancedProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Задает строковое значение свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetStringValue(StrValue)  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Description|  
|---------------|-----------------|  
|*StrValue*|Строка, указывающая значение дополнительного свойства.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Замечания  
 Тип значения свойства должен быть **строка** чтобы иметь возможность установить свойство в строковое значение.  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

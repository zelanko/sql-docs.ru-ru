---
description: Метод SetBoolValue (класс SqlServiceAdvancedProperty)
title: Метод SetBoolValue (класс sqlserviceadvancedproperty)
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db07b4e7dc83cffa60f5005195b9ac945620fe5b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427146"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a>Метод SetBoolValue (класс SqlServiceAdvancedProperty)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Задает логическое значение свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetBoolValue [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*булвалуе*|Логическое значение дополнительного свойства.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
 Чтобы задать логическое значение, свойство должно иметь логический тип.  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

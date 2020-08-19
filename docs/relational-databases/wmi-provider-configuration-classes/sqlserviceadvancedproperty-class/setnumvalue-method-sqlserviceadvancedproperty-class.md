---
description: Метод SetNumValue (класс SqlServiceAdvancedProperty)
title: Метод SetNumValue (класс sqlserviceadvancedproperty)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetNumValue Method (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetNumValue method
ms.assetid: a5e1056b-0b75-4ad6-99c1-89246010d815
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a67607dcf70b5d8a77eba098ba3090bd1ec552f8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427156"
---
# <a name="setnumvalue-method-sqlserviceadvancedproperty-class"></a>Метод SetNumValue (класс SqlServiceAdvancedProperty)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Задает числовое значение свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetNumValue(NumValue)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*NumValue*|Объект **uint32** , указывающий значение дополнительного свойства.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
 Чтобы для свойства можно было задать числовое значение, свойство должно иметь числовой тип.  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

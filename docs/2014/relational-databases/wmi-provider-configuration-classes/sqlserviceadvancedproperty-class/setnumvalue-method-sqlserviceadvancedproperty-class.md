---
title: Метод SetNumValue (класс SqlServiceAdvancedProperty) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetNumValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumValue method
ms.assetid: a5e1056b-0b75-4ad6-99c1-89246010d815
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7f31ef35b465467a00b6fe791c57d6d30f3e5069
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161014"
---
# <a name="setnumvalue-method-sqlserviceadvancedproperty-class"></a>Метод SetNumValue (класс SqlServiceAdvancedProperty)
  Задает числовое значение свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetNumValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServiceAdvancedProperty](sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*NumValue*|Объект `uint32`, указывающий значение дополнительного свойства.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
 Чтобы для свойства можно было задать числовое значение, свойство должно иметь числовой тип.  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

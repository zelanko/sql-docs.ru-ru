---
title: Метод SetStringValue (класс SqlServiceAdvancedProperty) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SetStringValue Method (SqlServiceAdvancedProperty Class )
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: a02d05f6-1072-4709-9ecc-e23e51c8c898
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a62c17ed296d7d35be0ee4954583d0f6ab7b1e29
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194897"
---
# <a name="setstringvalue-method-sqlserviceadvancedproperty-class-"></a>Метод SetStringValue (класс SqlServiceAdvancedProperty)
  Задает строковое значение свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlServiceAdvancedProperty](sqlserviceadvancedproperty-class.md) , представляющий дополнительное свойство.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*StrValue*|Строка, указывающая значение дополнительного свойства.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
 Чтобы отправить свойство строковому значению, значение свойства должно иметь тип `string`.  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
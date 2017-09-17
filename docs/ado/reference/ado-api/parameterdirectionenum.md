---
title: "ParameterDirectionEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c32176b7c9c5dc235c77e5f2363f1fc51ae9bb40
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Указывает, является ли [параметр](../../../ado/reference/ado-api/parameter-object.md) представляет входным параметром, выходным параметром, и входным и выходной параметр или возвращаемое значение хранимой процедуры.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|По умолчанию. Указывает, что параметр представляет входного параметра.|  
|**adParamInputOutput**|3|Указывает, что параметр представляет входных и выходных параметров.|  
|**adParamOutput**|2|Указывает, что параметр представляет выходной параметр.|  
|**adParamReturnValue**|4|Указывает, что параметр представляет возвращаемое значение.|  
|**adParamUnknown**|0|Указывает, что направление параметров неизвестен.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums.ParameterDirection.OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Свойство Direction](../../../ado/reference/ado-api/direction-property.md)|

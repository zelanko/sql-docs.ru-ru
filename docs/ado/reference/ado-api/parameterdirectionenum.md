---
title: ParameterDirectionEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd6f885b4e69ce73262961cf545eed2fa5a1c4da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Указывает, является ли [параметр](../../../ado/reference/ado-api/parameter-object.md) представляет входным параметром, выходным параметром, и входным и выходной параметр или возвращаемое значение хранимой процедуры.  
  
|Константа|Значение|Описание|  
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

---
title: ParameterDirectionEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3f62d2119764466cabb542d26849712d733453ba
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703265"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Указывает ли [параметр](../../../ado/reference/ado-api/parameter-object.md) представляет входного параметра, выходного параметра, как входные, так и выходной параметр или возвращаемое значение из хранимой процедуры.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|По умолчанию. Указывает, что данная строка представляет входной параметр.|  
|**adParamInputOutput**|3|Указывает, что данная строка представляет входных и выходных параметров.|  
|**adParamOutput**|2|Указывает, что данная строка представляет выходной параметр.|  
|**adParamReturnValue**|4|Указывает, что параметр представляет возвращаемое значение.|  
|**adParamUnknown**|0|Указывает, что направление параметра неизвестно.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
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

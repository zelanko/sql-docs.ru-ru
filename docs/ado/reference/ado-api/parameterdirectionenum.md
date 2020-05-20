---
title: Параметердиректионенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 88754f7dbd0064c765314d88b0fcc0d06f05bbb2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763405"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Указывает, представляет ли [параметр](../../../ado/reference/ado-api/parameter-object.md) входной параметр, выходной параметр, как входной, так и выходной параметр, или возвращаемое значение из хранимой процедуры.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адпараминпут**|1|По умолчанию. Указывает, что параметр представляет входной параметр.|  
|**адпараминпутаутпут**|3|Указывает, что параметр представляет как входной, так и выходной параметр.|  
|**адпарамаутпут**|2|Указывает, что параметр представляет выходной параметр.|  
|**адпарамретурнвалуе**|4|Указывает, что параметр представляет возвращаемое значение.|  
|**адпарамункновн**|0|Указывает, что направление параметра неизвестно.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Параметердиректион. INPUT|  
|Адоенумс. Параметердиректион. ИНПУТАУТПУТ|  
|Адоенумс. Параметердиректион. OUTPUT|  
|Адоенумс. Параметердиректион. RETURNVALUE|  
|Адоенумс. Параметердиректион. UNKNOWN|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Свойство Direction](../../../ado/reference/ado-api/direction-property.md)|

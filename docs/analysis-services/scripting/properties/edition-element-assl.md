---
title: Элемент Edition (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Edition Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Edition
helpviewer_keywords:
- Edition element
ms.assetid: 521e1286-097e-494f-b036-61047096e87e
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f163fe4b5fe5a7a173eddb78e49acc7bd3513b3b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="edition-element-assl"></a>Элемент Edition (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит доступный только для чтения выпуск экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] представленный [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Server>  
      ...  
      <Edition>...</Edition>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 **Edition** описывает, какой выпуск [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] установлен. Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Standard Edition Edition*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standard edition для 32-разрядных процессоров.|  
|*Enterprise*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition для 32-разрядных процессоров.|  
|*EnterpriseCore*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition: лицензирование по числу ядер для 32-разрядных процессоров.|  
|*BusinessIntelligence*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Business Intelligence edition для 32-разрядных процессоров.|  
|*Разработчик*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Developer edition для 32-разрядных процессоров|  
|*Оценки*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Evaluation edition для 64-разрядных процессоров.|  
|*Локальные*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Локальной версией для 32-разрядных процессоров.|  
|*Standard64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standard edition для 64-разрядных процессоров.|  
|*Enterprise64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition для 64-разрядных процессоров.|  
|*EnterpriseCore64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition: лицензирование по числу ядер для 64-разрядных процессоров.|  
|*BusinessIntelligence64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Выпуск business Intelligence для 64-разрядных процессоров.|  
|*Developer64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Developer edition для 64-разрядных процессоров|  
|*Evaluation64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Evaluation edition для 64-разрядных процессоров.|  
|*Local64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Локального edition для 64-разрядных процессоров.|  
  
 Перечисление, соответствующее разрешенным значениям для **ServerEdition** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ServerEdition>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Version &#40; ASSL &#41;](../../../analysis-services/scripting/properties/version-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

---
title: Элемент MasterDatasourceID (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0d15ac7183d703b0c02ffa1de5b5993810bd77b8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="masterdatasourceid-element-assl"></a>Элемент MasterDatasourceID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит идентификатор основного источника данных (ID) для [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database>  
   ...  
   <MasterDatasourceID>...</MasterDatasourceID>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для баз данных на удаленных экземпляров [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , содержащих удаленные секции **MasterDatasourceID** элемент содержит идентификатор источника данных, используемый для идентификации главного источника данных экземпляр [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , управляющий удаленными секциями.  
  
 Элемент, соответствующий родителю параметра **MasterDatasourceID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Database>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

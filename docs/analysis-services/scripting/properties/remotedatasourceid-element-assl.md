---
title: Элемент RemoteDatasourceID (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0ef82f0ef212f1a54dafefaaddaf6b87eccf4f83
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="remotedatasourceid-element-assl"></a>Элемент RemoteDatasourceID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает идентификатор (ID), указывающий на экземпляр источника данных OLAP [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , хранящий удаленную секцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Partition>  
      ...  
   <RemoteDatasourceID>...</RemoteDatasourceID>  
   ...  
</Partition>  
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
|Родительский элемент|[Секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если значение **RemoteDatasourceID** равно NULL, секция является локальной.  
  
 Элемент, соответствующий родителю параметра **RemoteDatasourceID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

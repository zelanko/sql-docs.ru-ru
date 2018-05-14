---
title: Элемент NullProcessing (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9e5fbc3682a614dc1599347ec030348ae10bb2c0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет способ обработки значений NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem>  
   ...  
   <NullProcessing>...</NullProcessing>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Автоматически*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Сохранить*|Сохраняет значение NULL.<br /><br /> Примечание: Это значение не поддерживается для мер числа различных объектов.|  
|*Ошибка*|Вызывает ошибку ключа NULL. Значение [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md) определяет реакцию экземпляра на эту ошибку.<br /><br /> Примечание: Это значение не поддерживается для мер.|  
|*UnknownMember*|Создает неизвестный элемент и вызывает ошибку преобразования ключа NULL. Значение [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md) определяет реакцию экземпляра на эту ошибку.<br /><br /> Примечание: Это значение не поддерживается для столбцов, связанных с мерами.|  
|*ZeroOrBlank*|Преобразует значение NULL в ноль (для элементов числовых данных) или пустую строку (для элементов строковых данных).<br /><br /> Примечание: Это значение обеспечивает совместимость с предыдущими версиями [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Автоматически*|Использует обработку по умолчанию, определенную для элемента:<br /><br /> *ZeroOrBlank* для элементов данных OLAP.<br /><br /> *UnknownMember* для элементов данных интеллектуального анализа данных.|  
  
 Перечисление, соответствующее разрешенным значениям для **NullProcessing** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

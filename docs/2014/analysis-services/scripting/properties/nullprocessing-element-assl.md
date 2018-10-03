---
title: Элемент NullProcessing (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NullProcessing Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c7fa4c851e6818a3c9607fed0fdb8b9c499a63d0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139895"
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Сохранить*|Сохраняет значение NULL. **Примечание:** это значение не поддерживается для мер числа различных объектов.|  
|*Ошибка*|Вызывает ошибку ключа NULL. Значение [NullKeyNotAllowed](nullkeynotallowed-element-assl.md) определяет реакцию экземпляра на эту ошибку. **Примечание:** это значение не поддерживается для мер.|  
|*UnknownMember*|Создает неизвестный элемент и вызывает ошибку преобразования ключа NULL. Значение [NullKeyConvertedToUnknown](nullkeyconvertedtounknown-element-assl.md) определяет реакцию экземпляра на эту ошибку. **Примечание:** это значение не поддерживается для столбцов, связанных с мерами.|  
|*ZeroOrBlank*|Преобразует значение NULL в ноль (для элементов числовых данных) или пустую строку (для элементов строковых данных). **Примечание:** это значение обеспечивает совместимость с предыдущими версиями [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Автоматически*|Использует обработку по умолчанию, определенную для элемента:<br /><br /> -   *ZeroOrBlank* для элементов данных OLAP.<br />-   *UnknownMember* для элементов данных интеллектуального анализа данных.|  
  
 Перечисление, соответствующее допустимым значениям элемента `NullProcessing` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  

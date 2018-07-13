---
title: Элемент KeyDuplicate (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- KeyDuplicate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyDuplicate
helpviewer_keywords:
- KeyDuplicate element
ms.assetid: d7000b8b-e81f-4401-8738-00c2e0f73a59
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6bbd445a1b362e7ae5bc7c12df3404efe1a781ea
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192450"
---
# <a name="keyduplicate-element-assl"></a>Элемент KeyDuplicate (ASSL)
  Определяет, каким образом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] обрабатывают ошибку повторяющегося ключа, возникающие во время обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyDuplicate>...</KeyDuplicate>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Пропустить ошибку*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Ошибки с повторяющимися значениями ключа возникают только во время обработки измерения, когда ключ атрибута появляется больше одного раза. Поскольку ключи атрибутов должны быть уникальны, службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] удаляют повторяющиеся записи. Ошибки с повторяющимися значениями ключа обычно свидетельствуют о дефектах модели измерения, в частности в связях между ее атрибутами.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке эту ошибку следует пропускать и продолжать выполнение.|  
|*Сообщить и продолжить*|При обработке следует создать отчет об этой ошибке и продолжать выполнение.|  
|*Сообщить и остановить выполнение*|При обработке следует создать отчет об этой ошибке и прервать выполнение.|  
  
 Перечисление, соответствующее допустимым значениям элемента `KeyDuplicate` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  

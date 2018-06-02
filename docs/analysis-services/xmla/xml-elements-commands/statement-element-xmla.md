---
title: Элемент Statement (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49238b50457a586bbf23cc75ee454003c57ac04e
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575026"
---
# <a name="statement-element-xmla"></a>Элемент Statement (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит запрос или инструкцию, отправляемых с помощью **Execute** метода с экземпляром служб Analysis Services.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Statement>...</Statement>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Инструкции** команда выполняет запрос или инструкцию на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают следующие языки.  
  
-   Многомерные выражения.  
  
-   Расширения интеллектуального анализа данных (многомерные выражения).  
  
-   Подмножество языка SQL.  
  
## <a name="see-also"></a>См. также
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

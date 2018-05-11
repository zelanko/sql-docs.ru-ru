---
title: Тип данных EmptyResult (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 514f1fd3b42ab65d4d05f91acd8d53674ee0c0ab
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="emptyresult-data-type-xmla"></a>Тип данных EmptyResult (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет производный тип данных, представляющий [корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемент, который не возвращает данные из [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis:empty  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Результирующий набор](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 В некоторых командах XML для аналитики (XMLA) возврат результата не предусмотрен или невозможен из-за ошибки. Команды XMLA, не возвращающие результатов, возвращают тип данных **EmptyResult** из пространства имен элемента **root** .  
  
## <a name="example"></a>Пример  
 В следующем примере представлен элемент **root** , возвращенный для пустого результата.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  

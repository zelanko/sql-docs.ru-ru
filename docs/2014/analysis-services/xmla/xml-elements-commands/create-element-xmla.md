---
title: Создать элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Create Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a3679fd48885b3538996b38286709e14b665bef0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247737"
---
# <a name="create-element-xmla"></a>Элемент Create (XML для аналитики)
  Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом `Execute` метод для создания объектов в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|AllowOverwrite|Необязательный `Boolean` атрибута. Если имеет значение True, объекты, определенные в элементе `ObjectDefinition`, могут заменять существующие объекты в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Если этот атрибут пропущен или имеет значение False, то при наличии существующего объекта возникает ошибка.|  
|Область действия|Необязательный `Enum` атрибута. Определяет срок жизни объектов, определенных в элементе `ObjectDefinition`. Если этот атрибут опускается, объекты, определенные в элементе `ObjectDefinition`, сохраняются в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Доступны следующие значения:<br /><br /> -   *Сеанс*<br />     Объекты, определенные в элементе `ObjectDefinition`, существуют только во время сеанса XML для аналитики (XMLA). **Примечание:** при использовании *сеанса* параметр `ObjectDefinition` элемент может содержать только [измерения](../../scripting/objects/dimension-element-assl.md), [куба](../../scripting/objects/cube-element-assl.md), или [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Элементы языка ASSL.|  
  
## <a name="remarks"></a>Примечания  
 Каждая операция `Create` создает для родительского объекта, указанного в элементе `ParentObject`, один главный объект. Если родительский элемент пропущен, предполагается, что им является целевой экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Если родитель главного объекта не является целевым экземпляром, возникает ошибка.  
  
## <a name="example"></a>Пример  
 В следующем примере в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создается пустая база данных с именем `Test Database`.  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>См. также  
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  

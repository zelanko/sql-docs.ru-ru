---
title: Изменить элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Alter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords:
- Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a9bdf13c64834100db14357a5a0ac7f47a6f9bf3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205794"
---
# <a name="alter-element-xmla"></a>Элемент Alter (XML для аналитики)
  Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом [Execute](../xml-elements-methods-execute.md) для изменения объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Alter Scope="enum" AllowCreate="boolean" ObjectExpansion="enum">  
      <Object>...</Object>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Alter>  
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
|Дочерние элементы|[Объект](../xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|AllowCreate|Необязательный атрибут типа `Boolean`. Показывает, необходимо ли создавать объекты, определенные в команде `Alter`, если их не существует.<br /><br /> Если установлено значение true, то объекты, определенные в элементе `ObjectDefinition`, будут созданы экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (в том случае, если они не существуют). Другими словами, если в экземпляре не существует нужных объектов, команда `Alter` обрабатывается точно так же, как и команда `Create`. <br /><br /> Если для этого атрибута не было задано значение или было задано значение `false`, то в том случае, если объектов не существует, будет возвращена ошибка.|  
|ObjectExpansion|Необязательный атрибут типа `Enum`. Определяет масштаб изменений, которые будут произведены методом `Execute`.<br /><br /> Если значение *ObjectProperties*, `ObjectDefinition` элемент должен содержать только полное описание основного объекта, который должен быть изменен, включая подчиненные второстепенных объектов. Подчиненные главные объекты изменяемого объекта затронуты не будут. **Примечание:** при использовании *ObjectProperties* параметра [ClrAssembly](../../scripting/data-type/assembly-data-type-assl.md) тип данных, [данных](../../scripting/objects/data-element-assl.md) элемент связанного [ ClrAssemblyFile](../../scripting/data-type/clrassemblyfile-data-type-assl.md) необходимо указать типы данных. Если параметр не указан, то `ClrAssembly` использует существующие файлы. <br /><br /> Если значение *ExpandFull*, `ObjectDefinition` элемент должен содержать не только определение изменяемого объекта, который должен быть изменен, но и определения всех главных объектов, являющихся его потомками объекта, который должен быть изменен. **Примечание:** *ExpandFull* нельзя использовать с [Server](../../scripting/objects/server-element-assl.md) элемент.|  
|Область действия|Необязательный атрибут типа `Enum`. Определяет срок жизни объектов, определенных в элементе `ObjectDefinition`.<br /><br /> Если значение *сеанса*, объекты, определенные в `ObjectDefinition` элемент существует только в течение сеанса XMLA. **Примечание:** при использовании *сеанса* параметр `ObjectDefinition` элемент может содержать только [измерения](../../scripting/objects/dimension-element-assl.md), [куба](../../scripting/objects/cube-element-assl.md), или [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Элементы языка ASSL. <br /><br /> Если этот атрибут опускается, объекты, определенные в элементе `ObjectDefinition`, сохраняются в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="remarks"></a>Примечания  
 Каждый `Alter` команда изменяет определение одного главного объекта, подчиняющегося родительскому объекту, заданному по [ParentObject](../xml-elements-properties/parentobject-element-xmla.md) элемент.  
  
## <a name="see-also"></a>См. также  
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  

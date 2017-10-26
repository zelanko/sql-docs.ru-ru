---
title: "Изменить элемент (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Alter Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords:
- Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70986afb0f916e150ec203e3beb48684d9902f02
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-element-xmla"></a>Элемент Alter (XML для аналитики)
  Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) для изменения объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|AllowCreate|Необязательный атрибут типа **Boolean** . Показывает, необходимо ли создавать объекты, определенные в команде **Alter** , если их не существует.<br /><br /> Если задано значение true, объекты, определенные в **ObjectDefinition** будут созданы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, если они еще не существует. Другими словами, если в экземпляре не существует нужных объектов, команда **Alter** обрабатывается точно так же, как и команда **Create** .<br /><br /> Если для этого атрибута не было задано значение или было задано значение **false**, то в том случае, если объектов не существует, будет возвращена ошибка.|  
|ObjectExpansion|Необязательный атрибут типа **Enum** . Определяет масштаб изменений, которые будут произведены методом **Execute** .<br /><br /> Если установлено значение *ObjectProperties*, элемент **ObjectDefinition** должен содержать только полное описание изменяемого главного объекта, включающее описания подчиненных ему второстепенных объектов. Подчиненные главные объекты изменяемого объекта затронуты не будут.<br /><br /> Примечание: При использовании *ObjectProperties* с [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) тип данных [данные](../../../analysis-services/scripting/objects/data-element-assl.md) элемент связанного [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) необходимо указать типы данных. Если параметр не указан, то **ClrAssembly** использует существующие файлы.<br /><br /> Если установлено значение *ExpandFull*, то в элементе **ObjectDefinition** должно содержаться не только определение изменяемого объекта, но и определения всех главных объектов, являющихся его потомками.<br /><br /> Примечание: *ExpandFull* параметр не может использоваться с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемента.|  
|Область действия|Необязательный атрибут типа **Enum** . Определяет срок жизни объектов, определенных в элементе **ObjectDefinition** .<br /><br /> Если установлено значение *Session*, то объекты, определенные в элементе **ObjectDefinition** , будут существовать только в течение сеанса XMLA.<br /><br /> Примечание: При использовании *сеанса* параметр **ObjectDefinition** элемент может содержать только [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md), [куба](../../../analysis-services/scripting/objects/cube-element-assl.md), или [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элементы языка ASSL.<br /><br /> Если этот атрибут опускается, объекты, определенные в **ObjectDefinition** , сохраняются в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.|  
  
## <a name="remarks"></a>Замечания  
 Каждый **Alter** команда изменяет определение одного главного объекта в родительский объект, определяемый [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md) элемента.  
  
## <a name="see-also"></a>См. также:  
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  


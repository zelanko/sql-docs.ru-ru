---
title: Изменить элемент (XMLA) | Документы Microsoft
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
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5ea2c3ed3105c66b0c0848138acb5941978dd9bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100704"
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
|ObjectExpansion|Необязательный атрибут типа `Enum`. Определяет масштаб изменений, которые будут произведены методом `Execute`.<br /><br /> Если значение *ObjectProperties*, `ObjectDefinition` должен содержать только полное описание основной объект должен быть изменен, включающее подчиненных ему второстепенных объектов. Подчиненные главные объекты изменяемого объекта затронуты не будут. **Примечание:** при использовании *ObjectProperties* с [ClrAssembly](../../scripting/data-type/assembly-data-type-assl.md) тип данных [данные](../../scripting/objects/data-element-assl.md) элемент связанного [ ClrAssemblyFile](../../scripting/data-type/clrassemblyfile-data-type-assl.md) необходимо указать типы данных. Если параметр не указан, то `ClrAssembly` использует существующие файлы. <br /><br /> Если значение *ExpandFull*, `ObjectDefinition` должен содержать не только определение объекта должен быть изменен, но также определения всех главных объектов, являющихся его потомками объекта должен быть изменен. **Примечание:** *ExpandFull* параметр не может использоваться с [сервера](../../scripting/objects/server-element-assl.md) элемента.|  
|Область действия|Необязательный атрибут типа `Enum`. Определяет срок жизни объектов, определенных в элементе `ObjectDefinition`.<br /><br /> Если значение *сеанса*, объекты, определенные в `ObjectDefinition` элемент существует только в течение сеанса XMLA. **Примечание:** при использовании *сеанса* параметр `ObjectDefinition` элемент может содержать только [измерения](../../scripting/objects/dimension-element-assl.md), [куба](../../scripting/objects/cube-element-assl.md), или [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Элементы языка ASSL. <br /><br /> Если этот атрибут опускается, объекты, определенные в элементе `ObjectDefinition`, сохраняются в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="remarks"></a>Примечания  
 Каждый `Alter` команда изменяет определение одного главного объекта в родительский объект, определяемый [ParentObject](../xml-elements-properties/parentobject-element-xmla.md) элемента.  
  
## <a name="see-also"></a>См. также  
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
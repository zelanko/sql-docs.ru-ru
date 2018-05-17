---
title: Создать элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb6a4e848b35a31feeef31bb8e304ba43a8577f3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="create-element-xmla"></a>Элемент Create (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит элементы языка сценариев служб Analysis Services (ASSL), используемые методом **Execute** метод для создания объектов в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|AllowOverwrite|Необязательный атрибут типа **Boolean** . Если задано значение True, объекты, определенные в **ObjectDefinition** элемент можно заменять существующие объекты в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Если этот атрибут пропущен или имеет значение False, то при наличии существующего объекта возникает ошибка.|  
|Область действия|Необязательный атрибут типа **Enum** . Определяет срок жизни объектов, определенных в элементе **ObjectDefinition** . Если этот атрибут опускается, объекты, определенные в **ObjectDefinition** , сохраняются в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Доступен следующий параметр:<br /><br /> *Сеанс*: объекты, определенные в **ObjectDefinition** элемент существует только в течение XML для аналитики (XMLA) сеанса.<br />                  Обратите внимание, что при использовании *сеанса* параметр **ObjectDefinition** элемент может содержать только [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md), [куба](../../../analysis-services/scripting/objects/cube-element-assl.md), или [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элементы языка ASSL.|  
  
## <a name="remarks"></a>Примечания  
 Каждая операция **Create** создает для родительского объекта, указанного в элементе **ParentObject** , один главный объект. Если родительский элемент пропущен, предполагается, что им является целевой экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Если родитель главного объекта не является целевым экземпляром, возникает ошибка.  
  
## <a name="example"></a>Пример  
 В следующем примере создается пустая база данных с именем **тестовую базу данных** на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
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
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

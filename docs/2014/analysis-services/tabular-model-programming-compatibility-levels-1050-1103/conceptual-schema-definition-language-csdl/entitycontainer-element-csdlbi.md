---
title: Элемент EntityContainer (CSDLBI) | Документация Майкрософт
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
ms.assetid: e328558e-16b0-4d4a-a79a-fdd3c9493595
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e7b477c8f972f277db921c7adb6f9511efb065c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275210"
---
# <a name="entitycontainer-element-csdlbi"></a>Элемент EntityContainer (CSDLBI)
  Элемент EntityContainer — сложный тип на основе типа языка CSDL EntityContainer, который определяет коллекцию сущностей в рамках единой модели данных. В приложении бизнес-аналитики модель данных, представленная элементом EntityContainer, может содержать несколько таблиц со столбцами, для которых объединены отношения, а также вычисления, меры и ключевые показатели эффективности. Он концептуально похож на базу данных или источник данных.  
  
 В элементе EntityContainer должен указываться каждый из типов сущностей, включенных в модель данных, включая таблицы и связи. Сведения об этих сущностях в моделях указаны в списке дочерних сущностей этого типа в элементе Entity. Дополнительные сведения см. в разделе [Элемент EntityType (CSDLBI)](entitytype-element-csdlbi.md).  
  
 Свойства, такие как параметры сортировки и язык, определяются на уровне элемента EntityContainer, а не на уровне отдельных объектов. Однако столбцы и текстовые атрибуты в пределах модели могут располагать заголовками или переводами на других языках.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В таблице ниже описаны элементы и атрибуты, определяющие EntityContainer.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Имя|Да|Имя модели данных.|  
|Заголовок|Нет|Описание базы данных или модели данных.|  
|Культура|Да|Строка, которая содержит код языка запроса.|  
|CompareOptions|Да|Параметры сортировки с учетом языка и сравнения строк для модели.|  
|DirectQueryMode|Нет|Перечисление, указывающее режим запроса при работе модели в режиме DirectQuery.|  
|Элемент EntitySet|Да|[Элемент EntitySet &#40;CSDLBI&#41;](entityset-element-csdlbi.md)|  
|Элемент AssociationSet|Нет|[Элемент AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)|  
  
## <a name="compareoptions-element"></a>Элемент CompareOptions  
 Атрибут CompareOptions определяет свойства параметров сортировки, которые применяются к модели данных. Свойства, заданные элементом CompareOptions, наследуются из параметров сортировки, учета японской азбуки и чувствительности к регистру, установленными в базе данных Analysis Services во время разработки модели. В следующей таблице описаны значения, которые включены в состав атрибута CompareOptions.  
  
|Значение|Описание|  
|-----------|-----------------|  
|IgnoreCase|Логическое значение, указывающее, следует ли при сравнении строк учитывать регистр.|  
|IgnoreNonSpace|Логическое значение, указывающее, следует ли при сравнении строк учитывать модифицирующие символы, отличные от пробела, например диакритические знаки.|  
|IgnoreKanaType|Логическое значение, указывающее, следует ли при сравнении строк учитывать вид каны.|  
|IgnoreWidth|Логическое значение, указывающее, следует ли при сравнении строк учитывать ширину символов.|  
  
## <a name="directquerymode"></a>DirectQueryMode  
 **Режим Directquery**  
  
 Простой тип DirectQueryMode определяет тип запроса, используемый по умолчанию, когда модель может получать данные напрямую из реляционного источника данных. Это свойство применимо только к табличным моделям, работающим в режиме DirectQuery. В следующей таблице приводятся возможные значения перечисления в режиме DirectQuery.  
  
|Значение|Описание|  
|-----------|-----------------|  
|InMemory|Показывает, что запросы к модели должны использовать данные в кэше.|  
|InMemoryWithDirectQuery|Показывает, что по умолчанию запросы к модели должны использовать данные из реляционного источника данных.|  
|DirectQuerywithInMemory|Показывает, что по умолчанию запросы к модели должны использовать данные в кэше.|  
|DirectQuery|Показывает, должны ли запросы к модели использовать данные только из реляционного источника данных.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 представлена часть табличной модели данных AdventureWorks.  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
       Name="DimEmployee"   
       EntityType="Sandbox.DimEmployee">  
   <bi:EntitySet />  
   </EntitySet>  
  
   <EntitySet   
     Name="DimProduct"   
       EntityType="Sandbox.DimProduct">  
    <bi:EntitySet />  
    </EntitySet>  
  
<bi:EntityContainer Caption="AWSimple" Culture="en-US">  
  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 Следующий пример для CSDLBI версии 1.1 является извлечением из куба операций Contoso.  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
      Name="Bike"   
      EntityType="Sandbox.Bike">  
    <bi:EntitySet Hidden="true" />  
   </EntitySet>  
…  
<bi:EntityContainer   
   Caption="CSDLTest"   
   Culture="en-US">  
<bi:CompareOptions   
   IgnoreCase="true" />  
</bi:EntityContainer>  
</EntityContainer>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент EntitySet &#40;CSDLBI&#41;](entityset-element-csdlbi.md)  
  
  

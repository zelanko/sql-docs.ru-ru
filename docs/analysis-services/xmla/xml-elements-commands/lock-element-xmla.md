---
title: Заблокировать элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a6524c4454eca42a771b2c3c87c2a6513804f720
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575246"
---
# <a name="lock-element-xmla"></a>Элемент Lock (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Блокирует указанный объект в экземпляре служб Analysis Services.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
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
|Дочерние элементы|[Идентификатор](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md), [режим](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md), [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда **Lock** блокирует объект для совместного или монопольного использования в контексте текущей активной транзакции. Явно выполнять команду **Lock** могут только администраторы базы данных или администраторы сервера. Блокировка объекта не позволяет фиксировать транзакции, пока она не будет снята. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают два типа блокировок: совмещаемые и монопольные. Дополнительные сведения о поддерживаемых типах блокировки [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], в разделе [элемент Mode &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] позволяют блокировать только базы данных. **Объекта** элемент должен содержать ссылку на объект [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных. Если элемент **Object** не указан или если элемент **Object** ссылается на объект, отличающийся от базы данных, возникает ошибка.  
  
 Другие команды неявно выполняют **блокировки** на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных. Любая операция по чтению данных или метаданных из базы данных, например любой метод **Discover** или метод **Execute** , запускающий команду **Statement** , неявно устанавливает совмещаемую блокировку для базы данных. Любая транзакция, фиксирующая изменения в данных или метаданных объекта в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, например **Execute** метод, выполняемый **Alter** неявным образом устанавливает монопольную блокировку на База данных.  
  
 Все блокировки удерживаются в контексте текущей транзакции. После фиксации или отката текущей транзакции все блокировки, определенные в рамках транзакции, автоматически снимаются.  
  
## <a name="see-also"></a>См. также
 [Разблокировать элемент &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

---
title: Элемент NotifyTableChange (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 125cea75f5c892cd30e3f346c0b755ab8de55ae5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="notifytablechange-element-xmla"></a>Элемент NotifyTableChange (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Уведомляет экземпляр служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , что в таблицах указанного источника данных произошло изменение.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <NotifyTableChange>  
      <Object>...</Object>  
      <TableNotifications>...</TableNotifications>  
   </NotifyTableChange>  
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
|Дочерние элементы|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **NotifyTableChange** команда позволяет клиентскому приложению явно уведомить [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, что один или несколько таблиц, содержащихся в источнике данных были изменены. Для упреждающего кэширования такое уведомление указывает, что объекты реляционного OLAP (ROLAP), основанные на этих таблицах, должны быть проверены и обновлены.  
  
 Этот метод уведомления лучше всего подходит для объектов ROLAP, основанных на представлениях или именованных запросах, определенных в представлении источника данных, изменения в которых сложно выявлять и отслеживать.  
  
 **Объекта** должен ссылаться на источник данных в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных. Если элемент **Object** ссылается на объект, отличный от источника данных, возникает ошибка.  
  
 Дополнительные сведения об упреждающем кэшировании см. в разделе [Упреждающее кэширование (секции)](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>См. также:  
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

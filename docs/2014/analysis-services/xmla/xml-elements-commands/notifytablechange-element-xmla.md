---
title: Элемент NotifyTableChange (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NotifyTableChange Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords:
- NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25d060b73f7fb5999d4eb04faaa209eb7713f9d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224442"
---
# <a name="notifytablechange-element-xmla"></a>Элемент NotifyTableChange (XML для аналитики)
  Уведомляет экземпляр служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] изменения, произведенного в таблицах указанного источника данных.  
  
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
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Объект](../xml-elements-properties/object-element-xmla.md), [TableNotifications](../xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `NotifyTableChange` позволяет клиентскому приложению явно уведомить экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] о том, что одна или несколько таблиц в источнике данных были изменены. Для упреждающего кэширования такое уведомление указывает, что объекты реляционного OLAP (ROLAP), основанные на этих таблицах, должны быть проверены и обновлены.  
  
 Этот метод уведомления лучше всего подходит для объектов ROLAP, основанных на представлениях или именованных запросах, определенных в представлении источника данных, изменения в которых сложно выявлять и отслеживать.  
  
 Элемент `Object` должен ссылаться на источник данных в базе данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Если элемент `Object` ссылается на объект, отличный от источника данных, возникает ошибка.  
  
 Дополнительные сведения об упреждающем кэшировании см. в разделе [Упреждающее кэширование (секции)](../../multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>См. также  
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  

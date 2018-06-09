---
title: Элемент безопасности (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c4ea0e1f9bfab567c792bdd7b233bea038e87f54
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576247"
---
# <a name="security-element-xmla"></a>Элемент Security (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает, как для резервного копирования или восстановления определений безопасности, такие как роли и разрешения, во время [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) или [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*skipMembership*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [восстановления](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Безопасности** определяет, являются ли определения безопасности, такие как роли и разрешения, определенные в базе данных служб Analysis Services резервного копирования или восстановления во время выполнения, соответственно, **резервного копирования** или **Восстановить** команды. Этот элемент также определяет, распространяются ли команды **Backup** и **Restore** на учетные записи пользователей и группы Windows, являющиеся членами определений безопасности.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*skipMembership*|Включить определения безопасности, но исключить сведения о членстве при выполнении команд **Backup** или **Restore** .|  
|*CopyAll*|Включить определения безопасности и сведения о членстве при выполнении команд **Backup** или **Restore** .|  
|*IgnoreSecurity*|Исключить определения безопасности при выполнении команд **Backup** или **Restore** .|  
  
## <a name="see-also"></a>См. также
 [Элемент SynchronizeSecurity &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

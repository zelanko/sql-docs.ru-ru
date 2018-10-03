---
title: Элемент Security (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Security Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords:
- Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 784a3f6b56c0372897b984c5fac4e8915cb53ebc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111979"
---
# <a name="security-element-xmla"></a>Элемент Security (XML для аналитики)
  Указывает способ резервного копирования или восстановления определений безопасности, таких как роли и разрешения, во время [резервного копирования](../xml-elements-commands/backup-element-xmla.md) или [восстановить](../xml-elements-commands/restore-element-xmla.md) команды.  
  
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
|Родительские элементы|[Резервное копирование](../xml-elements-commands/backup-element-xmla.md), [восстановления](../xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `Security` Определяет ли определения безопасности, такие как роли и разрешения, определенные в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных резервного копирования или восстановления при выполнении, соответственно, `Backup` или `Restore` команда. Этот элемент также определяет, распространяются ли команды `Backup` и `Restore` на учетные записи пользователей и группы Windows, являющиеся членами определений безопасности.   
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*skipMembership*|Включить определения безопасности, но исключить сведения о членстве при выполнении команд `Backup` или `Restore`.|  
|*CopyAll*|Включить определения безопасности и сведения о членстве при выполнении команд `Backup` или `Restore`.|  
|*IgnoreSecurity*|Исключить определения безопасности при выполнении команд `Backup` или `Restore`.|  
  
## <a name="see-also"></a>См. также  
 [Элемент SynchronizeSecurity &#40;XML для Аналитики&#41;](security-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  

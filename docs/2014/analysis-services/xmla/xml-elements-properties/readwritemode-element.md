---
title: Элемент ReadWriteMode | Документы Microsoft
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
helpviewer_keywords:
- ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 88ebc7e23fc3ec4aad0d8273464636354958217a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195459"
---
# <a name="readwritemode-element"></a>Элемент ReadWriteMode
  Свойство базы данных `ReadWriteMode` указывает, в каком режиме работает база данных: `ReadWrite` или `ReadOnly`. Эти значения являются единственными допустимыми для данного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|ReadWrite|  
|Количество элементов|0—1: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](database-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Базы данных создаются только в режиме `ReadWrite`. Базы данных не могут создаваться в режиме `ReadOnly`.  
  
 Значением элемента `ReadWriteMode` может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Только для чтения*|База данных не может быть ни обновлена, ни изменена.|  
|*ReadWrite*|База данных может изменяться и обновляться.|  
  
## <a name="see-also"></a>См. также  
 [Элемент Attach](../xml-elements-commands/attach-element.md)   
 [Присоединение и отсоединение баз данных служб Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных служб Analysis Services](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Режимы ReadWriteModes базы данных](../../multidimensional-models/database-readwritemodes.md)   
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
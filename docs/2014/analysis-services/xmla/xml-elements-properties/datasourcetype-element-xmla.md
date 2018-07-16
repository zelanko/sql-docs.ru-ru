---
title: Элемент DataSourceType (XMLA) | Документация Майкрософт
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
- DataSourceType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords:
- DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c911f2a0e224cb8ccc9e7fa5b32a89a972fd1c26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207674"
---
# <a name="datasourcetype-element-xmla"></a>Элемент DataSourceType (XML для аналитики)
  Указывает ли [расположение](location-element-xmla.md) элемент, заданный для [восстановить](../xml-elements-commands/restore-element-xmla.md) или [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) команда является локальным или удаленным.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Удаленный*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Расположение](location-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `DataSourceType` определяет, содержит ли элемент `Location` локальный или удаленный источник данных. Дополнительные сведения о резервном копировании и восстановлении удаленных секций, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Локальный*|Элемент `Location` определяет локальный источник данных. При использовании этого значения команды `Restore` и `Synchronize` используют определенные в элементе `Location` сведения для обновления источника данных, полученного или из файлов резервной копии, заданной в элементе `File` для команды `Backup`, или из базы данных, заданной в элементе `Source` для команды `Synchronize`. Источник данных определяется элементом `DataSourceID` элемента `Location`.<br /><br /> Это значение позволяет объектам, пользующимся реляционным хранилищем OLAP (ROLAP), после восстановления или синхронизации использовать другую базу данных для хранения данных и метаданных. **Примечание:** данных ROLAP, например данных в таблицах измерения или таблицах обратной записи, не восстанавливаются и синхронизируются. Восстанавливаются и синхронизируются только метаданные объектов ROLAP.|  
|*Удаленный*|Элемент `Location` определяет удаленный источник данных. При использовании этого значения команды `Restore` и `Synchronize` используют определенные в элементе `Location` сведения для восстановления или синхронизации в удаленном экземпляре, определенном элементом `File` элемента `Backup`, удаленных секций, полученных или из файлов резервной копии, заданной в элементе `Source` для команды `Synchronize`, или из базы данных, заданной в элементе `DataSourceID` для команды `Location`.|  
  
## <a name="see-also"></a>См. также  
 [Элемент ConnectionString &#40;XML для Аналитики&#41;](connectionstring-element-xmla.md)   
 [Элемент DataSourceID &#40;XML для Аналитики&#41;](id-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  

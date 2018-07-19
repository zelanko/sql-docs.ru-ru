---
title: Синхронизировать элемент (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 11804b9b6ca9ac430bdb47c0b9050b8c6995cf7f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007185"
---
# <a name="synchronize-element-xmla"></a>Элемент Synchronize (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Синхронизирует базу данных служб Analysis Services с другой существующей базой данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [расположения](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [источника](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда **Synchronize** синхронизирует целевую базу данных с экземпляром источника и базой данных, указанными в элементе **Source** . По желанию команда **Synchronize** может синхронизировать удаленные секции, определенные в базе данных-источнике.  
  
 В зависимости от режима хранения, используемого для объектов в файле резервной копии, команда **Synchronize** синхронизирует данные так, как это показано в следующей таблице.  
  
|Режим хранения|Сведения|  
|------------------|-----------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|Гибридный OLAP (HOLAP)|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время выполнения команды **Synchronize** на базу данных-источник ставится блокировка на чтение, а на целевую базу данных — блокировка на запись. Обе блокировки снимаются после выполнения команды **Synchronize** .  
  
 Дополнительные сведения о синхронизации баз данных, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Резервное копирование элемента &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Элемент Batch &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Элемент Parallel &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Элемент RESTORE &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

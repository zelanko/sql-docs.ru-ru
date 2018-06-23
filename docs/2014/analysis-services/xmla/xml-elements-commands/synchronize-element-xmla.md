---
title: Синхронизировать элемент (XMLA) | Документы Microsoft
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
- Synchronize Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronize
- urn:schemas-microsoft-com:xml-analysis#Synchronize
- http://schemas.microsoft.com/analysisservices/2003/engine#Synchronize
helpviewer_keywords:
- Synchronize command
ms.assetid: 9401323c-feff-409a-a9da-94aee47e0563
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 367d237cab7ea63b85e000433742d866466b3f62
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191498"
---
# <a name="synchronize-element-xmla"></a>Элемент Synchronize (XML для аналитики)
  Синхронизирует [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных с другой существующей базой данных.  
  
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
|Дочерние элементы|[ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [расположения](../xml-elements-properties/locations-element-xmla.md), [источника](../xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `Synchronize` синхронизирует целевую базу данных с экземпляром источника и базой данных, указанными в элементе `Source`. По желанию команда `Synchronize` может синхронизировать удаленные секции, определенные в базе данных-источнике.  
  
 В зависимости от режима хранения, используемого для объектов в файле резервной копии, команда `Synchronize` синхронизирует данные так, как это показано в следующей таблице.  
  
|Режим хранения|Сведения|  
|------------------|-----------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|Гибридный OLAP (HOLAP)|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время выполнения команды `Synchronize` на базу данных-источник ставится блокировка на чтение, а на целевую базу данных — блокировка на запись. Обе блокировки снимаются после выполнения команды `Synchronize`.  
  
 Дополнительные сведения о синхронизации баз данных см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование элемента &#40;XML для Аналитики&#41;](backup-element-xmla.md)   
 [Элемент Batch &#40;XML для Аналитики&#41;](batch-element-xmla.md)   
 [Параллельные элемент &#40;XML для Аналитики&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Элемент RESTORE &#40;XML для Аналитики&#41;](restore-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
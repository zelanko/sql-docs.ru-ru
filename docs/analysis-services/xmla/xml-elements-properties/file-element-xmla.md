---
title: "Файл элемента (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: File Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords: File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d098aa61edb8d51b7a3868b21b768b7ab286e48c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="file-element-xmla"></a>Элемент File (XML для аналитики)
  Определяет файл для использования в родительском [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) или [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) команду, либо в родительском [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [восстановления](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Файл** элемент содержит UNC-имя файла и его родительский элемент определяет использование **файл** элемента.  
  
 Для **резервного копирования** команд, **файл** определяет имя файла резервной копии, созданные **резервного копирования** команды. Если путь не указан как часть имени файла, путь, указанный в **BackupDir** свойство конфигурации для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используется. Если указанный файл уже существует, возникает ошибка, если не **AllowOverwrite** родителя **резервного копирования** набор команд **True**.  
  
 Для **восстановить** команд, **файл** определяет имя файла резервной копии, которую требуется восстановить **восстановить** команды.  
  
 Для **расположение** элементов, **файл** элемент описывает удаленный файл резервной копии для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр, который содержит удаленные секции. Дополнительные сведения о резервном копировании и восстановлении удаленных секций см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Элемент AllowOverwrite &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

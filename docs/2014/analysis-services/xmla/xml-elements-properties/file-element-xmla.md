---
title: Файл элемента (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords:
- File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5ae3390405bc7a722934f3b3fb3652825b2ea03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125454"
---
# <a name="file-element-xmla"></a>Элемент File (XML для аналитики)
  Определяет файл для использования в родительском [резервного копирования](../xml-elements-commands/backup-element-xmla.md) или [восстановить](../xml-elements-commands/restore-element-xmla.md) команду, либо в родительском [расположение](location-element-xmla.md) элемент.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../xml-elements-commands/backup-element-xmla.md), [расположение](location-element-xmla.md), [восстановления](../xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `File` Элемент содержит UNC-имя файла и его родительский элемент определяет использование `File` элемент.  
  
 Для команд `Backup` элемент `File` определяет имя файла резервной копии, создаваемого командой `Backup`. Если путь не указан как часть имени файла, путь, указанный в `BackupDir` свойство конфигурации для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используется. Если указанный файл уже существует и значение элемента `AllowOverwrite` родительской команды `Backup` не имеет значение `True`, произойдет ошибка.  
  
 Для команд `Restore` элемент `File` определяет имя файла резервной копии, предназначенной для восстановления командой `Restore`.  
  
 Для элементов `Location` элемент `File` описывает удаленный файл резервной копии для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], который содержит данные удаленных секций. Дополнительные сведения о резервном копировании и восстановлении удаленных секций, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент AllowOverwrite &#40;XML для Аналитики&#41;](allowoverwrite-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  

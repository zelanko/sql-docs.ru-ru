---
title: Элемент Location (XML для Аналитики) | Документы Microsoft
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
- Location Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.location
- urn:schemas-microsoft-com:xml-analysis#Location
- http://schemas.microsoft.com/analysisservices/2003/engine#Location
helpviewer_keywords:
- Location element
ms.assetid: cea5e776-f435-425a-9bce-812d727a2b71
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 51b0838b9843658b4081f9464c63274631ed74be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192969"
---
# <a name="location-element-xmla"></a>Элемент Location (XML для аналитики)
  Содержит сведения об удаленном сервере для родительской [резервного копирования](../xml-elements-commands/backup-element-xmla.md), [восстановить](../xml-elements-commands/restore-element-xmla.md), или [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Location>  
```  
  
```  
  
<File>...</File> <!-- for Backup and Restore only -->  
<DataSourceID>...</DataSourceID>  
<DataSourceType>...</DataSourceType> <!-- for Restore and Synchronize only -->  
<ConnectionString>...</ConnectionString> <!-- for Restore and Synchronize only -->  
<Folders>...</Folders> <!-- for Restore and Synchronize only -->  
```  
  
```  
  
   </Location>  
   ...  
</Backup>  
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
|Родительские элементы|[Резервное копирование](../xml-elements-commands/backup-element-xmla.md), [восстановить](../xml-elements-commands/restore-element-xmla.md), [синхронизации](../xml-elements-commands/synchronize-element-xmla.md)|  
  
## <a name="child-elements"></a>Дочерние элементы  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Резервное копирование](id-element-xmla.md), [файла](file-element-xmla.md)|  
|[Восстановление](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [файл](file-element-xmla.md), [папки](folders-element-xmla.md)|  
|[Synchronize](../xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [папки](folders-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для `Backup` команд, `Location` элемент предоставляет сведения о создании удаленного файла резервной копии для удаленного экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Для команд `Restore` элемент `Location` предоставляет сведения об идентификации и соединении с удаленным экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], а также об удаленном файле резервной копии, используемом для восстановления удаленных секций на этом экземпляре.  
  
 Для команд `Synchronize` элемент `Location` описывает либо источник данных, который будет использоваться целевым экземпляром, либо удаленный экземпляр, определенный на экземпляре источника, который должен быть синхронизирован с целевым экземпляром, в зависимости от значения элемента `DataSourceType` для родительской команды `Synchronize`.  
  
 Дополнительные сведения о резервном копировании и восстановлении удаленных экземпляров см. в разделе [резервное копирование и восстановление объектов (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент BackupRemotePartitions &#40;XML для Аналитики&#41;](backupremotepartitions-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
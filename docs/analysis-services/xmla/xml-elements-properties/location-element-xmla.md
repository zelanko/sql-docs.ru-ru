---
title: Элемент Location (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ea049b70ee2aa41a1e2fc1e7204be658f4f0bd6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="location-element-xmla"></a>Элемент Location (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит сведения об удаленном сервере для родительской команды [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) .  
  
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
|Родительские элементы|[Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|См. таблицу ниже.|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|[DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [File](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)|  
|[Восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [File](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [Folders](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|[Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [Folders](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для **резервного копирования** команд, **расположение** элемент предоставляет сведения о создании удаленного файла резервной копии для удаленного экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Для **восстановить** команд, **расположение** элемент предоставляет сведения об идентификации и соединении с удаленным [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, а также использовать для восстановления удаленных удаленного файла резервной копии секций на этом удаленном экземпляре.  
  
 Для команд **Synchronize** элемент **Location** описывает либо источник данных, который будет использоваться целевым экземпляром, либо удаленный экземпляр, определенный на экземпляре источника, который должен быть синхронизирован с целевым экземпляром, в зависимости от значения элемента **DataSourceType** для родительской команды **Synchronize** .  
  
 Дополнительные сведения о резервном копировании и восстановлении удаленных экземпляров см. в разделе [Резервное копирование и восстановление объектов (XML для аналитики)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Элемент BackupRemotePartitions & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

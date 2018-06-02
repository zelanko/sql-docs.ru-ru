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
ms.openlocfilehash: 4953981e7657706a986e9a2407f6786ff676a854
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575606"
---
# <a name="location-element-xmla"></a>Элемент Location (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит сведения об удаленном сервере для родительской [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
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
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [синхронизации](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|См. таблицу ниже.|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|[DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [файла](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)|  
|[Восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [файл](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [папки](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|[Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md), [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md), [DataSourceType](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md), [папки](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для **резервного копирования** команд, **расположение** элемент предоставляет сведения о создании удаленного файла резервной копии на удаленном экземпляре служб Analysis Services.  
  
 Для **восстановить** команд, **расположение** элемент предоставляет сведения об идентификации и соединении с удаленным [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, а также использовать для восстановления удаленных удаленного файла резервной копии секций на этом удаленном экземпляре.  
  
 Для команд **Synchronize** элемент **Location** описывает либо источник данных, который будет использоваться целевым экземпляром, либо удаленный экземпляр, определенный на экземпляре источника, который должен быть синхронизирован с целевым экземпляром, в зависимости от значения элемента **DataSourceType** для родительской команды **Synchronize** .  
  
 Дополнительные сведения о резервном копировании и восстановлении удаленных экземпляров см. в разделе [резервное копирование и восстановление объектов (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Элемент BackupRemotePartitions &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

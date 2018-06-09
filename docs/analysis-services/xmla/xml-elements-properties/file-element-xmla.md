---
title: Файл элемента (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb80a091c9b9585a6efc29088d15139db7033efb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575196"
---
# <a name="file-element-xmla"></a>Элемент File (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет файл для использования в родительском [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) или [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) команду, либо в родительском [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
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
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [восстановления](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Файл** элемент содержит UNC-имя файла и его родительский элемент определяет использование **файл** элемента.  
  
 Для **резервного копирования** команд, **файл** определяет имя файла резервной копии, созданные **резервного копирования** команды. Если путь не указан как часть имени файла, путь, указанный в **BackupDir** используется свойство конфигурации для экземпляра служб Analysis Services. Если указанный файл уже существует, возникает ошибка, если не **AllowOverwrite** родителя **резервного копирования** набор команд **True**.  
  
 Для **восстановить** команд, **файл** определяет имя файла резервной копии, которую требуется восстановить **восстановить** команды.  
  
 Для **расположение** элементов, **файл** элемент описывает удаленный файл резервной копии для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр, который содержит удаленные секции. Дополнительные сведения о резервном копировании и восстановлении удаленных секций см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Элемент AllowOverwrite &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

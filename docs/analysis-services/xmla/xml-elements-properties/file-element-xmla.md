---
title: Файл элемента (XMLA) | Документация Майкрософт
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
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970002"
---
# <a name="file-element-xmla"></a>Элемент File (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет файл для использования в родительском [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) или [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) команду, либо в родительском [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [восстановления](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Файл** элемент содержит UNC-имя файла и его родительский элемент определяет использование **файл** элемент.  
  
 Для **резервного копирования** команды, **файл** определяет имя файла резервной копии, созданные **резервного копирования** команды. Если путь не указан как часть имени файла, путь, указанный в **BackupDir** используется свойство конфигурации для экземпляра служб Analysis Services. Если указанный файл уже существует, возникает ошибка, если не **AllowOverwrite** родителя **резервного копирования** команда имеет значение **True**.  
  
 Для **восстановить** команды, **файл** определяет имя файла резервной копии, которую требуется восстановить **восстановить** команды.  
  
 Для **расположение** элементов, **файл** элемент описывает удаленный файл резервной копии для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр, который содержит удаленные секции. Дополнительные сведения о резервном копировании и восстановлении удаленных секций, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Элемент AllowOverwrite &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

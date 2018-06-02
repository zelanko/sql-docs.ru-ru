---
title: Восстановить элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ea1bd6b12c605309f9c6c78151bed08c37149372
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577017"
---
# <a name="restore-element-xmla"></a>Элемент Restore (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Восстанавливает базу данных служб Analysis Services из файла резервной копии.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Restore>  
      <DatabaseName>...</DatabaseName>  
      <DatabaseID>...</DatabaseID>  
      <File>...</File>  
      <Security>...</Security>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <Locations>...</Locations>  
      <DbStorageLocation>...</DbStorageLocation>  
   </Restore>  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md), [DatabaseName](../../../analysis-services/xmla/xml-elements-properties/databasename-element-xmla.md), [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [файл](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [расположения](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [пароля](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md), [Безопасности](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md), [DbStorageLocation](../../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)|  
  
## <a name="remarks"></a>Примечания  
 **Восстановить** восстанавливает [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в **DatabaseName** элемент из файла резервной копии и при необходимости восстановление удаленных секций из удаленных файлов резервной копии.  
  
 В зависимости от режима хранения, используемого для объектов в файле резервной копии, команда **Restore** восстанавливает данные, перечисленные в следующей таблице.  
  
|Режим хранения|Сведения|  
|------------------|-----------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|Гибридный OLAP (HOLAP)|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время **восстановить** команды монопольную блокировку на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в **DatabaseName** элемента. Блокировка снимается после выполнения команды **Restore** .  
  
 Дополнительные сведения о резервном копировании и восстановлении баз данных см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду восстановления, должен иметь разрешение на чтение из папки резервного копирования, указанной для каждого восстанавливаемого файла. Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , которая не установлена на сервере, пользователь также должен быть членом роли сервера для этого экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Чтобы перезаписать базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (Администратор)" в восстанавливаемой базе данных.  
  
> [!NOTE]  
>  После восстановления существующей базы данных пользователь, выполнявший восстановление, может утратить доступ к этой базе данных. Потеря доступа может произойти в случае, если на время создания резервной копии этот пользователь не был членом роли сервера и роли базы данных с разрешением «Полный доступ (Администратор)».  
  
## <a name="see-also"></a>См. также
 [Резервное копирование элемента &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Элемент Batch &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Параллельные элемент &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

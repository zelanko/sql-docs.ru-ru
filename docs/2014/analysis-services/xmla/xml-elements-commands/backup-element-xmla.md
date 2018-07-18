---
title: Резервное копирование элемент (XMLA) | Документация Майкрософт
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
- Backup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a571681f52fb34e55df238229f659aa883bc84ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215654"
---
# <a name="backup-element-xmla"></a>Элемент Backup (XML для аналитики)
  Создает резервные копии [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных в файл резервной копии.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Backup>  
      <Object>...</Object>  
      <File>...</File>  
      <Security>...</Security>  
      <ApplyCompression>...</ApplyCompression>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <BackupRemotePartitions>...</BackupRemotePartitions>  
      <Locations>...</Locations>  
   </Backup>  
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
|Дочерние элементы|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../xml-elements-properties/backupremotepartitions-element-xmla.md), [файл](../xml-elements-properties/file-element-xmla.md), [расположения](../xml-elements-properties/locations-element-xmla.md), [ Объект](../xml-elements-properties/object-element-xmla.md), [пароль](../xml-elements-properties/password-element-xmla.md), [безопасности](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 `Backup` Команда создает резервную [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в [объект](../xml-elements-properties/object-element-xmla.md) файла резервной копии, и при необходимости создает резервные копии удаленных секций удаленных файлов резервной копии. Если элемент `Object` ссылается не на базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], возникает ошибка.  
  
 Какие сведения `Backup` команда создает резервную копию зависит от режима хранения, используемой объектами в базе данных. В следующей таблице показано, резервная копия каких данных создается в каждом режиме хранения.  
  
|Режим хранения|Данные, попадающие в резервную копию|  
|------------------|-----------------------------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|Гибридный OLAP (HOLAP)|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время `Backup` команды на устанавливается совмещаемая блокировка [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в `Object` элемент. Совмещаемая блокировка снимается после `Backup` выполнения команды.  
  
 Несколько `Backup` команды могут выполняться параллельно, если они включены в [параллельных](../xml-elements-properties/parallel-element-xmla.md) коллекцию [пакета](batch-element-xmla.md) команды. Коллекция `Parallel` позволяет одновременно создавать несколько резервных копий базы данных.  
  
 Дополнительные сведения о резервном копировании и восстановлении баз данных, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду резервного копирования, должен иметь разрешение на запись в папку резервного копирования, указанную для каждого копируемого файла. Кроме того, пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (администратор)" в базе данных, для которой создается резервная копия.  
  
## <a name="see-also"></a>См. также  
 [Элемент RESTORE &#40;XML для Аналитики&#41;](restore-element-xmla.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](synchronize-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  

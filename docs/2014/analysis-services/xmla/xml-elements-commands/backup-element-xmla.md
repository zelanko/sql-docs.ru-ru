---
title: Резервное копирование элемента (XMLA) | Документы Microsoft
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
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bd1f2317c28acd2e6037520334168491ec0bbcbe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195660"
---
# <a name="backup-element-xmla"></a>Элемент Backup (XML для аналитики)
  Создает резервную копию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных в файл резервной копии.  
  
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
 `Backup` Команда создает резервную копию [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в [объекта](../xml-elements-properties/object-element-xmla.md) файл резервной копии и при необходимости выполняет резервное копирование удаленных секций, удаленных файлов резервной копии элемента. Если элемент `Object` ссылается не на базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], возникает ошибка.  
  
 Какие сведения `Backup` команда создает резервную копию зависит от режима хранения, используемого объектами базы данных. В следующей таблице показано, резервная копия каких данных создается в каждом режиме хранения.  
  
|Режим хранения|Данные, попадающие в резервную копию|  
|------------------|-----------------------------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|Гибридный OLAP (HOLAP)|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время `Backup` команды, совмещаемая блокировка на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в `Object` элемент. Совмещаемая блокировка снимается после `Backup` выполнения команды.  
  
 Несколько `Backup` команды могут выполняться параллельно, если они включены в [параллельных](../xml-elements-properties/parallel-element-xmla.md) коллекцию [пакета](batch-element-xmla.md) команды. Коллекция `Parallel` позволяет одновременно создавать несколько резервных копий базы данных.  
  
 Дополнительные сведения о резервном копировании и восстановлении баз данных см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду резервного копирования, должен иметь разрешение на запись в папку резервного копирования, указанную для каждого копируемого файла. Кроме того, пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (администратор)" в базе данных, для которой создается резервная копия.  
  
## <a name="see-also"></a>См. также  
 [Элемент RESTORE &#40;XML для Аналитики&#41;](restore-element-xmla.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](synchronize-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
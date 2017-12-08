---
title: "Резервное копирование элемента (XMLA) | Документы Microsoft"
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
apiname: Backup Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords: Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ed85939848e2304cec9651245815c3848da5aa04
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
|Количество элементов|0–n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md), [файл](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [расположения](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [пароль](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md), [безопасности](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **Резервного копирования** команда создает резервную копию [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) файл резервной копии и при необходимости выполняет резервное копирование удаленных секций, удаленных файлов резервной копии элемента. Если **объекта** элемент ссылается на объект, отличный от [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, возникает ошибка.  
  
 Данные, попадающие в резервную копию, создаваемую командой **Backup** , зависят от режима хранения, используемого объектами базы данных. В следующей таблице показано, резервная копия каких данных создается в каждом режиме хранения.  
  
|Режим хранения|Данные, попадающие в резервную копию|  
|------------------|-----------------------------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|гибридный OLAP (HOLAP).|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время **резервного копирования** команды, совмещаемая блокировка на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в **объекта** элемент. Совмещаемая блокировка снимается после выполнения команды **Backup** .  
  
 Несколько **резервного копирования** команды могут выполняться параллельно, если они включены в [параллельных](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md) коллекцию [пакета](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) команды. Коллекция **Parallel** позволяет одновременно создавать несколько резервных копий базы данных.  
  
 Дополнительные сведения о резервном копировании и восстановлении баз данных см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду резервного копирования, должен иметь разрешение на запись в папку резервного копирования, указанную для каждого копируемого файла. Кроме того, пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (администратор)" в базе данных, для которой создается резервная копия.  
  
## <a name="see-also"></a>См. также:  
 [Восстановить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Синхронизировать элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

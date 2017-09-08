---
title: "Элемент AllowOverwrite (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AllowOverwrite Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.allowoverwrite
- urn:schemas-microsoft-com:xml-analysis#EndSession
helpviewer_keywords:
- AllowOverwrite element
ms.assetid: e7e92481-5f29-47f2-9efd-4e5e60c002bb
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c47939bfc376589512fad8d4eb5367c9dc7fe5fb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="allowoverwrite-element-xmla"></a>Элемент AllowOverwrite (XML для аналитики)
  Определяет ли родительский [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) или [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) команда пытается перезаписывать целевой файл или базу данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <AllowOverwrite>...</AllowOverwrite>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|False|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [восстановления](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Для команд **Backup** элемент **AllowOverwrite** определяет, будут ли они перезаписывать файл резервной копии, заданный в элементе **File** .  
  
 Для **восстановить** элементов, **AllowOverwrite** определяет, может ли команда перезаписать [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в **DatabaseName** элемента.  
  
## <a name="see-also"></a>См. также:  
 [Элемент DatabaseName &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/databasename-element-xmla.md)   
 [Элемент файла &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

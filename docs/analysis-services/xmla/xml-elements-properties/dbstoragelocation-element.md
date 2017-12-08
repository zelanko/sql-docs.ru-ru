---
title: "Элемент DbStorageLocation | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cf7859b90400b1dc6962e16c4d2c4e43f5290b75
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbstoragelocation-element"></a>Элемент DbStorageLocation
  Указывает папку, в которой службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создают все файлы данных базы данных и метаданных, а также управляют ими.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database>  
...  
   <ddl100_100:DbStorageLocation>...</ddl100_100:DbStorageLocation>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|""|  
|Количество элементов|0—1: Необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 В свойстве базы данных **DbStorageLocation** должен быть задан путь к существующей папке в формате UNC или пустая строка. Пустая строка является папкой данных сервера, используемой по умолчанию. Если папка не существует, при выполнении команд **Create**, **Attach**или **Alter** возникнет ошибка.  
  
 Кроме того, нельзя настроить свойство базы данных **DbStorageLocation** таким образом, чтобы оно указывало на папку данных сервера или на одну из вложенных в нее папок. Если местоположение указывает на папку данных сервера или на одну из вложенных в нее папок, при выполнении команд **Create**, **Attach**или **Alter** возникнет ошибка.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Подключение и отключение баз данных служб Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  

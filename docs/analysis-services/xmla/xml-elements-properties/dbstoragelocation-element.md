---
title: "Элемент DbStorageLocation | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
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
ms.openlocfilehash: bf2bc5ab8c0419260049d8e588fd491a50099135
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dbstoragelocation-element"></a>Элемент DbStorageLocation
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Указывает папку, где [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создает и управляет ими, все базы данных файлы данных и метаданных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database>  
...  
   <ddl100_100:DbStorageLocation>...</ddl100_100:DbStorageLocation>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|""|  
|Количество элементов|0—1: Необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 В свойстве базы данных **DbStorageLocation** должен быть задан путь к существующей папке в формате UNC или пустая строка. Пустая строка является папкой данных сервера, используемой по умолчанию. Если папка не существует, при выполнении команд **Create**, **Attach**или **Alter** возникнет ошибка.  
  
 Кроме того, нельзя настроить свойство базы данных **DbStorageLocation** таким образом, чтобы оно указывало на папку данных сервера или на одну из вложенных в нее папок. Если местоположение указывает на папку данных сервера или на одну из вложенных в нее папок, при выполнении команд **Create**, **Attach**или **Alter** возникнет ошибка.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Подключение и отключение баз данных служб Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  

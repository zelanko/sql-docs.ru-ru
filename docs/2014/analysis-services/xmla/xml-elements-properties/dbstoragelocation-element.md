---
title: Элемент DbStorageLocation | Документы Microsoft
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
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 651dc0424c492efefa7828ae327f9bdcf837ed77
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100479"
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
|Тип данных и длина|String|  
|Значение по умолчанию|""|  
|Количество элементов|0—1: Необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](database-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `DbStorageLocation` Базы данных должен указывать существующий путь UNC или пустая строка. Пустая строка является папкой данных сервера, используемой по умолчанию. Если папка не существует, при выполнении команд `Create`, `Attach` или `Alter` возникнет ошибка.  
  
 Кроме того `DbStorageLocation` свойство базы данных не может быть присвоено указывало на папку данных сервера или любой из ее вложенных папках. Если местоположение указывает на папку данных сервера или на одну из вложенных в нее папок, при выполнении команд `Create`, `Attach` или `Alter` возникнет ошибка.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Подключение и отключение баз данных служб Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
---
title: Элемент DbStorageLocation | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdee1fc2d62f63eb70e5aecd47c32693a9fbd155
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173924"
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
 `DbStorageLocation` Свойство базы данных должно быть присвоено существующий путь UNC или пустая строка. Пустая строка является папкой данных сервера, используемой по умолчанию. Если папка не существует, при выполнении команд `Create`, `Attach` или `Alter` возникнет ошибка.  
  
 Кроме того `DbStorageLocation` базы данных не может указывать на папку данных сервера или любой из ее вложенных папках. Если местоположение указывает на папку данных сервера или на одну из вложенных в нее папок, при выполнении команд `Create`, `Attach` или `Alter` возникнет ошибка.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Подключение и отключение баз данных служб Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  

---
title: Элемент DatabaseName (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DatabaseName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.databasename
- http://schemas.microsoft.com/analysisservices/2003/engine#DatabaseName
- urn:schemas-microsoft-com:xml-analysis#DatabaseName
helpviewer_keywords:
- DatabaseName element
ms.assetid: 5cfd9a1f-da53-497a-b677-c51be4641bd0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4727f3554b654687484e6bd273a0d88e557215e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172684"
---
# <a name="databasename-element-xmla"></a>Элемент DatabaseName (XML для аналитики)
  Идентифицирует [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, которую требуется восстановить родительской [восстановить](../xml-elements-commands/restore-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Restore>  
   ...  
   <DatabaseName>...</DatabaseName>  
   ...  
</Restore>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Восстановить](../xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `DatabaseName` определяет базу данных, в которой команда `Restore` восстанавливает файл резервной копии. Если этот элемент не задан или содержит пустую строку, используется имя базы данных, имеющееся в файле резервной копии.  
  
 Наличие этой базы данных на целевом экземпляре приводит к возникновению ошибки, если элементу `AllowOverwrite` родительской команды `Restore` не присвоено значение `True`.  
  
## <a name="see-also"></a>См. также  
 [Элемент AllowOverwrite &#40;XML для Аналитики&#41;](allowoverwrite-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  

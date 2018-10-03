---
title: Элемент Attach | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- Attach command
ms.assetid: a315d1f1-e220-4296-97cb-6d35606b9640
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eda22adcd9760fbeb01e009b0a8d9692f7e5d333
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105404"
---
# <a name="attach-element"></a>Элемент Attach
  Присоединяет [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, которая ранее была отсоединена от текущего экземпляра сервера или из другого экземпляра, для текущего экземпляра сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Attach>  
      <Folder>...</Folder>  
            <ReadWriteMode>...</ReadWriteMode>  
            <Password>...</Password>  
   </Attach>  
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
|Дочерние элементы|[Папка](../xml-elements-properties/folder-element-xmla.md)<br /><br /> [ReadWriteMode](../xml-elements-properties/readwritemode-element.md)<br /><br /> [Пароль](../xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Элемент detach](detach-element.md)   
 [Присоединение и отсоединение баз данных служб Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных служб Analysis Services](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Режимы ReadWriteModes базы данных](../../multidimensional-models/database-readwritemodes.md)   
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  

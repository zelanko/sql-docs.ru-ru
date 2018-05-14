---
title: Удаление команды (TMSL) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b45148559ae80d2c5821faad1fb124ee63b5866
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="delete-command-tmsl"></a>Удаление команды (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Удаление базы данных или объекта в текущей базе данных.   
Он удаляет указанный объект и все дочерние объекты и коллекции. Если объект не существует, команда вызывает ошибку.  
  
## <a name="request"></a>Запрос  
 Удаляемый объект указан с помощью путь к объекту. Например удаление раздела необходимо указать объекты таблиц и баз данных, расположенные перед ним.  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",   
      "partition": "may2011"   
    }   
  }   
}   
```  
  
 Можно удалить следующие объекты:  
  
 [Объект базы данных &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016"  
    }   
  }   
}   
```  
  
 [Источники данных объекта &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureworksDW2016",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    }  
  }  
}  
```  
  
 [Объект Tables &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",  
    }   
  }   
}   
```  
  
 [Объект секции &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",   
      "partition": "may2011"   
    }   
  }   
}   
```  
  
 [Объект роли &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "role": "Data Reader"  
    }   
  }   
}   
```  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="examples"></a>Примеры  
 **Пример 1** -удаление базы данных.  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureWorksDW2016"  
    }  
  }  
}  
```  
  
 **Пример 2** -удаление подключения.  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureWorksDW2016",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    }  
  }  
}  
```  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS.  Например, можно щелкнуть правой кнопкой мыши существующую базу данных > **сценарий** > **скрипта базы данных в качестве** > **DELETE в**.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе [языке скриптов табличных моделей &#40;TMSL&#41; ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) для дополнительной информации о том, что поддерживается.  

## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

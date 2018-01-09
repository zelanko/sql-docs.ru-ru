---
title: "MergePartitions, команда (TMSL) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dd568426-a415-41bf-b1e9-ea2261babf81
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7960dbd174c0f959439029dc05cd16efbc42f319
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mergepartitions-command-tmsl"></a>MergePartitions, команда (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Выполняет слияние данных из одного или нескольких исходных секций в целевую секцию, а затем удаляет исходной секции. SQL-запрос целевой секции не будет обновляться в ходе операции слияния. Чтобы убедиться, что последующая обработка секции получает все данные, следует изменить запрос, чтобы он выбирает все данные в объединенной секции.  
  
## <a name="request"></a>Запрос  
 Необходимо указать базу данных, таблицы и исходной и целевой секциях. Объединять можно только секции из одной таблицы.  
  
```  
{   
  "mergePartitions": {   
    "object": {   
      "database": "salesdatabase",   
      "table": "sales",   
      "partition": "may2015"   
    },   
    "sources": [   
      {   
        "database": "salesdatabase",   
        "table": "Sales",   
        "partition": "partition1"   
      },   
      {   
        "database": "salesdatabase",   
        "table": "Sales",   
        "partition": "partition2"   
      }   
    ]   
  }   
}  
  
```  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40; XML для Аналитики &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS.  Например, можно щелкнуть **сценарий** в диалоговом окне Управление секциями.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе [языке скриптов табличных моделей &#40; TMSL &#41; Справочник по](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) для дополнительной информации о том, что поддерживается  

## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Создание секций табличной модели и управление ими (табличные службы SSAS)](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  

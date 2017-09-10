---
title: "Последовательность команд (TMSL) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 898d6ec2-9b40-441b-be2b-5728d1d2882e
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e7fc7f1541131ac6a8e7249940a31104e50f0b09
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sequence-command-tmsl"></a>Команда sequence (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Используйте **последовательности** команду для запуска набор последовательных операций в пакетном режиме в экземпляре служб Analysis Services.  Вся команда и всех его компонентов необходимо выполнить в порядке, для успешного выполнения транзакции.  
  
 Следующие команды могут выполняться последовательно, за исключением для **обновление** команду, которая выполняется в параллельном режиме для одновременной обработки нескольких объектов.  
  
-   [Создать команду &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)  
  
-   [Команду CreateOrReplace &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)  
  
-   [ALTER, команда &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)  
  
-   [Удалить команду &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)  
  
-   [Обновить команды &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)  
  
-   [Команда BACKUP &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)  
  
-   [Восстановление команд &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)  
  
-   [Присоединение команда &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)  
  
-   [Detach, команда &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)  
  
## <a name="request"></a>Запрос  
 **maxParallelism** — это необязательное свойство, определяющее, является ли **обновление** операции выполняются последовательно или параллельно.  
  
 Поведение по умолчанию является по возможности используйте столько параллелизма. Внедрив **обновление** в **последовательность**, можно задать точное число потоков, используемых во время обработки, в том числе ограничения операции только в одном потоке.  
  
> [!NOTE]  
>  Целое число, присвоенное **maxParallelism** определяет максимальное число потоков, используемых во время обработки. Допустимые значения — любое положительное целое число. При установке значения 1 equals не параллельных (использует один поток).  
  
 Только **обновление** выполняется параллельно. При изменении **maxParallelism** использовать фиксированное количество потоков, не забудьте просмотреть ее свойства на [обновить команды &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md) чтобы понять возможные последствия. Можно задать свойства в виде, понижающие параллелизма, даже в том случае, если доступны несколько потоков. Следующие типы обновления обеспечит оптимальную степень параллелизма:  
  
-   Во-первых определяют обновление для всех объектов с помощью ClearValues  
  
-   Затем укажите обновления для всех объектов с помощью DataOnly  
  
-   Последнее определяют обновление для всех объектов, Full, Calculate, автоматическое или добавить  
  
 Любое изменение на это приведет к разрыву параллелизма.  
  
```  
{   
  "sequence":    
    {   
      "maxParallelism": 3,   
      "operations": [   
        {   
          "mergepartitions": {   
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
        },   
        {   
          "refresh": {   
            "type": "calculate",   
            "object": {   
             "database": "salesdatabase"   
            }   
          }   
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
  
 Не удается создать готовый сценарий для этой команды в среде SSMS. Вместо этого можно запустить с примером, или написать собственный.  
  
 [ \[MS-SSAS-T\]: табличный SQL Server Analysis Services (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов . В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе ([языке скриптов табличных моделей &#40; TMSL &#41; Ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) для дополнительной информации о том, что поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

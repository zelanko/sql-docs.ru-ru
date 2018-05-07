---
title: Последовательность команд (TMSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/12/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 898d6ec2-9b40-441b-be2b-5728d1d2882e
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2faf4ebe89154d43d9af45f751d00002fd4b3277
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sequence-command-tmsl"></a>Команда sequence (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Используйте **последовательности** команду для запуска набор последовательных операций в пакетном режиме в экземпляре служб Analysis Services.  Вся команда и всех его компонентов необходимо выполнить в порядке, для успешного выполнения транзакции.  
  
 Следующие команды могут выполняться последовательно, за исключением для **обновление** команду, которая выполняется в параллельном режиме для одновременной обработки нескольких объектов.  
  
-   [Создание команды &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)  
  
-   [Команду CreateOrReplace &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)  
  
-   [ALTER, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)  
  
-   [Удаление команды &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)  
  
-   [Команда "Обновить" &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)  
  
-   [Резервное копирование команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)  
  
-   [Команды RESTORE &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)  
  
-   [Команда присоединения &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)  
  
-   [Detach, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)  
  
## <a name="request"></a>Запрос  
 **maxParallelism** — это необязательное свойство, определяющее, является ли **обновление** операции выполняются последовательно или параллельно.  
  
 Поведение по умолчанию является по возможности используйте столько параллелизма. Внедрив **обновление** в **последовательность**, можно задать точное число потоков, используемых во время обработки, в том числе ограничения операции только в одном потоке.  
  
> [!NOTE]  
>  Целое число, присвоенное **maxParallelism** определяет максимальное число потоков, используемых во время обработки. Допустимые значения — любое положительное целое число. При установке значения 1 equals не параллельных (использует один поток).  
  
 Только **обновление** выполняется параллельно. При изменении **maxParallelism** использовать фиксированное количество потоков, не забудьте просмотреть ее свойства на [команда "Обновить" &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md) чтобы понять возможные последствия. Можно задать свойства в виде, понижающие параллелизма, даже в том случае, если доступны несколько потоков. Следующие типы обновления обеспечит оптимальную степень параллелизма:  
  
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
            "objects": {   
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
 Этот элемент команды используется в инструкции [выполнить метод &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Не удается создать готовый сценарий для этой команды в среде SSMS. Вместо этого можно запустить с примером, или написать собственный.  
  
 [ \[MS-SSAS-T\]: табличный SQL Server Analysis Services (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов . В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе ([языке скриптов табличных моделей &#40;TMSL&#41; ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) для дополнительной информации о том, что поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

---
title: "Команды в табличной модели язык сценариев (TMSL) | Документы Microsoft"
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4eb07192-6f53-4426-830a-d63a945dbcab
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71b44ae1e5f8e5db2859bb4d3b2457c752de4dc6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="tmsl-reference---commands"></a>Ссылка TMSL - команды

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Команды можно выполнить на конечной точке XML для Аналитики, составление определений объектов в табличной модели языка скриптов (TMSL), к базам данных табличной модели с помощью JSON.   В разделе [определений объектов в табличной модели язык сценариев &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) список объектов, используемых с помощью следующих команд.  
  
## <a name="object-operations"></a>Операций с объектами  
  
|||  
|-|-|  
|[ALTER, команда &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)|Внесите изменения встроенного объекта без указания полное определение.|  
|[Создать команду &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)|Создает новый объект, включая его потомков.|  
|[Команду CreateOrReplace &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)|Создать или заменить части определения объекта. Необходимо указать полное определение.|  
|[Удалить команду &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)|Удаление объекта, включая его потомков.|  
  
## <a name="data-refresh-operations"></a>Операции обновления данных  
  
|||  
|-|-|  
|[MergePartitions, команда &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)|Слияние секций целевой в источник и удалите целевой объект.|  
|[Обновить команды &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)|Обработка базы данных, таблицы или секции.|  
  
## <a name="scripting"></a>Создание скриптов  
  
|||  
|-|-|  
|[Команда Sequence &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)|Пакетные операции последовательно или параллельно|  
  
## <a name="database-management-operations"></a>Операции с базой данных управления  
  
|||  
|-|-|  
|[Присоединение команда &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)|Добавляет файл на сервер.|  
|[Detach, команда &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)|Удаляет файл из серверов.|  
|[Команда BACKUP &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)|Создает файл резервной копии базы данных.|  
|[Восстановление команд &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)|Восстанавливает базу данных на сервер.|  
|[Синхронизировать команды &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/synchronize-command-tmsl.md)|Синхронизирует базу данных служб Analysis Services с другой базой данных.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Установка поставщиков данных служб Analysis Services &#40; Объекты AMO, ADOMD.NET, MSOLAP &#41;](../../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  

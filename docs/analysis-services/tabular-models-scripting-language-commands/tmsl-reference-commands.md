---
title: Команды в табличной модели язык сценариев (TMSL) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9c36ba09aa19aa8abc1c21ea8c870dbfe2d24c9e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="tmsl-reference---commands"></a>Ссылка TMSL - команды
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Команды можно выполнить на конечной точке XML для Аналитики, составление определений объектов в табличной модели языка скриптов (TMSL), к базам данных табличной модели с помощью JSON.   В разделе [определений объектов в языке скриптов табличных моделей &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) список объектов, используемых с помощью следующих команд.  
  
## <a name="object-operations"></a>Операций с объектами  
  
|||  
|-|-|  
|[ALTER, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)|Внесите изменения встроенного объекта без указания полное определение.|  
|[Создание команды &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)|Создает новый объект, включая его потомков.|  
|[Команду CreateOrReplace &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)|Создать или заменить части определения объекта. Необходимо указать полное определение.|  
|[Удаление команды &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)|Удаление объекта, включая его потомков.|  
  
## <a name="data-refresh-operations"></a>Операции обновления данных  
  
|||  
|-|-|  
|[MergePartitions, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)|Слияние секций целевой в источник и удалите целевой объект.|  
|[Команда "Обновить" &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)|Обработка базы данных, таблицы или секции.|  
  
## <a name="scripting"></a>Создание скриптов  
  
|||  
|-|-|  
|[Последовательность команд &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)|Пакетные операции последовательно или параллельно|  
  
## <a name="database-management-operations"></a>Операции с базой данных управления  
  
|||  
|-|-|  
|[Команда присоединения &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)|Добавляет файл на сервер.|  
|[Detach, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)|Удаляет файл из серверов.|  
|[Резервное копирование команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)|Создает файл резервной копии базы данных.|  
|[Команды RESTORE &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)|Восстанавливает базу данных на сервер.|  
|[Команда синхронизации &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/synchronize-command-tmsl.md)|Синхронизирует базу данных служб Analysis Services с другой базой данных.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Установка поставщиков данных служб Analysis Services &#40;AMO, ADOMD.NET, MSOLAP&#41;](../../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  

---
title: Определения объектов в табличной модели язык сценариев (TMSL) | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de968c32f8c00132157a5b1b7a6682adc7148446
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851749"
---
# <a name="tmsl-reference---tabular-objects"></a>Справочник по TMSL — табличные объекты
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Приложения, создание, использование и администрирование табличных баз данных или, подключиться к экземпляру SQL Server 2016 Analysis Services в табличном режиме, могут использовать модель языка скриптов табличной (TMSL) для команд и объектные представления в формате JSON.  
  
 В этой статье описываются основные объекты TMSL схемы, используемой в скрипты, созданные по SQL Server Management Studio, SQL Server Data Tools (SSDT) и объекты AMO PowerShell.  
  
 Определения объектов в формате JSON и используются в TMSL команд, таких как Create, Alter и удалить. См. в разделе [команды на языке Tmsl &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) для получения списка команд.  
  
## <a name="main-objects"></a>Основные объекты  
 Ниже приведен список наиболее часто используемые объекты в сценарии TMSL.  
  
|||  
|-|-|  
|[Объект базы данных &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Определяет табличной базы данных с уровнем совместимости 1200 или более поздней версии, на основе модели того же уровня.|  
|[Объект модели &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Определяет табличной модели с уровнем совместимости 1200 или выше.|  
|[Объект DataSources &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Определяет соединение с источником данных, используемые во время импорта для загрузки модели, либо для запросы к серверу, если модель находится в режиме DirectQuery.|  
|[Объект Tables &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Указывает таблицы модели.|  
|[Объект partitions &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Определяет хранение строк таблицы, а также вычисляемые таблицы.|  
|[Объект Relationships &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Определяет связи между таблицами.|  
|[Объект roles &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Определяет разрешения, членства и фильтров безопасности, управляющие доступом к данным и операциям.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

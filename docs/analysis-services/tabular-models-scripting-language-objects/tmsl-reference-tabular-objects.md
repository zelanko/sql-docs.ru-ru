---
title: Определения объектов в табличной модели язык сценариев (TMSL) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f9d8f8eea0786eb0713db0ae3d5d53279323116
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="tmsl-reference---tabular-objects"></a>Ссылка TMSL - табличных объектов
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Приложения, создание, использование и администрирование табличных баз данных или, подключитесь к экземпляру SQL Sever 2016 Analysis Services в табличном режиме, могут использовать табличной модели языка скриптов (TMSL) для команд и представления объектов в формате JSON.  
  
 В этой статье приведены основные объекты схемы TMSL, используемых в скриптах, созданных SQL Server Management Studio, SQL Server Data Tools (SSDT) и объекты AMO PowerShell.  
  
 Определения объектов в формате JSON и используются в TMSL команды Create, Alter и удалить. В разделе [команд в языке скриптов табличных моделей &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) список команд.  
  
## <a name="main-objects"></a>Основные объекты  
 В следующей таблице приведен список наиболее часто используемых объектов в сценарии TMSL.  
  
|||  
|-|-|  
|[Объект базы данных &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Определяет табличной базы данных на уровне совместимости 1200 или выше, на основе модели одного уровня.|  
|[Объект модели &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Определяет табличной модели на уровне совместимости 1200 или выше.|  
|[Источники данных объекта &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Определяет соединение с источником данных, используемые при импорте, чтобы загрузить модель или запросы к серверу при использовании модели в режиме DirectQuery.|  
|[Объект Tables &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Указывает таблицы модели.|  
|[Объект секции &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Определяет хранилище строк таблицы, а также вычисляемые таблицы.|  
|[Объект связи &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Определяет связи между таблицами.|  
|[Объект роли &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Определяет разрешения, членство и фильтры безопасности, управляющие доступом к данным и операциям.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

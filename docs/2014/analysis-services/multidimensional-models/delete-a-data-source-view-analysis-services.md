---
title: Удалить представление источника данных (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9750751a23e4322a4a48ec0c1c227cf2df16f1c7
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66075427"
---
# <a name="delete-a-data-source-view-analysis-services"></a>Удаление представления источников данных (службы Analysis Services)
  При отсутствии необходимости использования файла представления источников данных (DSV) в проекте OLAP его можно удалить из проекта среды [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 Удаление DSV необратимо. Восстановление удаленного источника DSV в проекте среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] невозможно.  
  
 Файлы представления источников данных (DSV), от которых зависят другие объекты, не могут быть удалены из базы данных среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , открытой в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] в режиме «в сети». Для удаления DSV из проекта, который имеет подключение к базе данных, запущенной на сервере, прежде всего необходимо удалить все объекты базы данных среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , зависящие от самого DSV.  
  
 Удаление DSV сделает недействительными все зависящие от него объекты среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , поэтому перед удалением DSV обратите внимание на список всех связанных с ним объектов. Внимательно изучите список объектов, убедитесь, что в нем отсутствуют объекты, необходимые для дальнейшего использования.  
  
 ![Удаление объектов-диалоговое окно](../media/ssas-olapdsv-deleteobjects.gif "диалоговое окно «Удаление объектов»")  
  
## <a name="see-also"></a>См. также  
 [Представления источников данных в многомерных моделях](data-source-views-in-multidimensional-models.md)   
 [Изменение свойств в представлении источника данных (службы Analysis Services)](change-properties-in-a-data-source-view-analysis-services.md)  
  
  

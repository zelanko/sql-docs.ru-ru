---
title: О SQL Server Analysis Services | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: overview
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 704c2f1638676bd838c7aac367a1b610143fd85d
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707042"
---
# <a name="about-sql-server-analysis-services"></a>О SQL Server Analysis Services

Службы Analysis Services — это ядро аналитических данных, используемых в решение о поддержке и бизнес-аналитике. Он предоставляет корпоративного уровня данных семантических моделей бизнес-отчетах и клиентских приложений, таких как Power BI, Excel, отчеты и другие средства визуализации данных Reporting Services.  

Типичный рабочий процесс включает создание проекта модели табличных или многомерных данных в Visual Studio, развертывание модели в качестве базы данных к экземпляру сервера, Настройка повторяющегося обработки данных и назначение разрешений на доступ к данным конечным пользователем. Когда она будет готова к работе, ваш семантическую модель данных может осуществляться клиентских приложений, поддерживающих служб Analysis Services в качестве источника данных.  

Службы Analysis Services можно найти в двух разных платформ: 

**Azure Analysis Services** -поддерживает табличные модели на уровне совместимости 1200 и выше. DirectQuery, секции, безопасность на уровне строк, двунаправленные связи и переводы полностью поддерживаются. Дополнительные сведения см. в разделе [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).

**SQL Server Analysis Services** -поддерживает табличные модели на всех уровнях совместимости, многомерных моделях, интеллектуальный анализ данных и Power Pivot для SharePoint.
 
 ## <a name="documentation-by-area"></a>Документация по разделам  
Как правило [документации по службам аналитики Azure](https://docs.microsoft.com/azure/analysis-services/) входит в состав документации Azure. Если вас интересует с табличными моделями в облаке, лучше начать прямо отсюда. Это статье и документация в этом разделе является главным образом для SQL Server Analysis Services. Тем не менее по крайней мере для табличных моделей, как создавать и развертывать проекты табличной модели является так же, независимо от используемой платформы. В этих разделах, чтобы получить дополнительные сведения см.

   
*  [Сравнение табличных и многомерных решений](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
*  [Установка SQL Server Analysis Services](../analysis-services/instances/install-windows/install-analysis-services.md)
*  [Табличные модели](../analysis-services/tabular-models/tabular-models-ssas.md)  
*  [Многомерные модели](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
*  [Интеллектуальный анализ данных](../analysis-services/data-mining/data-mining-ssas.md)  
*  [Power Pivot для SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
*  [Руководства](../analysis-services/analysis-services-tutorials-ssas.md)   
*  [Управление сервером](../analysis-services/instances/analysis-services-instance-management.md)    
*  [Документация для разработчиков](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
*  [Технический справочник](../analysis-services/powershell/technical-reference-ssas.md)

См. также

[Документация по Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)   
[Документация по SQL Server](../sql-server/sql-server-technical-documentation.md)

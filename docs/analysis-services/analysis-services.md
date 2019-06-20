---
title: О SQL Server Analysis Services | Документация Майкрософт
ms.date: 12/05/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: overview
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2cd892ad41beba2b5715b3a7186ae5e44bb7911
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63206355"
---
# <a name="about-sql-server-analysis-services"></a>Сведения о SQL Server Analysis Services

Службы Analysis Services — это подсистема аналитики данных, используемых в принятии решений и бизнес-аналитике. Он предоставляет корпоративного уровня семантические модели данных для бизнес-отчеты и клиентские приложения, например Power BI, Excel, отчеты служб Reporting Services и других инструментах визуализации данных.

Типичный рабочий процесс включает в себя создание проекта модели табличных или многомерных данных в Visual Studio, развертывания моделей в качестве базы данных к экземпляру сервера, Настройка повторяющегося обработки данных и назначение разрешений на доступ к данным конечным пользователем. Когда она готова к работе, в семантическую модель данных может осуществляться клиентскими приложениями, которые поддерживают Analysis Services в качестве источника данных.

Службы Analysis Services доступна в двух разных платформ:

**Службы Azure Analysis Services** -поддерживает табличные модели на уровнях совместимости 1200 и выше. DirectQuery, секции, безопасность на уровне строк, двунаправленные связи и переводы полностью поддерживаются. Дополнительные сведения см. в разделе [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).

**SQL Server Analysis Services** -поддерживают табличные модели на всех уровнях совместимости, многомерных моделях, интеллектуальный анализ данных и Power Pivot для SharePoint.

## <a name="documentation-by-area"></a>Документация по разделам

В общем случае [документации по Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/) входит в состав документации по Azure. Если вы заинтересованы в табличных моделях в облаке, лучше начать с этого. Этой статье и на документацию в этом разделе подходит в основном для SQL Server Analysis Services. Тем не менее по крайней мере для табличных моделей, как создавать и развертывать проекты табличной модели очень похоже на, независимо от платформы, которую вы используете. Просмотрите эти разделы, чтобы узнать больше.

- [Сравнение табличных и многомерных решений](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)
- [Установка SQL Server Analysis Services](../analysis-services/instances/install-windows/install-analysis-services.md)
- [Табличные модели](../analysis-services/tabular-models/tabular-models-ssas.md)
- [Многомерные модели](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)
- [Интеллектуальный анализ данных](../analysis-services/data-mining/data-mining-ssas.md)
- [Power Pivot для SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)
- [Руководства](../analysis-services/analysis-services-tutorials-ssas.md)
- [Управление сервером](../analysis-services/instances/analysis-services-instance-management.md)
- [Документация для разработчиков](analysis-services-developer-documentation.md)
- [Технический справочник](https://docs.microsoft.com/bi-reference/)

#### <a name="see-also"></a>См. также

[Документация по Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)
[документации по SQL Server](../sql-server/sql-server-technical-documentation.md)

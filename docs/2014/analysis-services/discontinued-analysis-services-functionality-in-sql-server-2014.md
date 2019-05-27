---
title: Неподдерживаемые функции служб Analysis Services в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- discontinued functionality [Analysis Services]
- unsupported features [Analysis Services]
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 616c39d03ff8081c209a80dcca912d831bcef1ff
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66081676"
---
# <a name="discontinued-analysis-services-functionality-in-sql-server-2014"></a>Неподдерживаемые функции служб Analysis Services в SQL Server 2014
  В этой статье описаны функции служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которые больше недоступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>Неподдерживаемые функции в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
  
|Category|Устаревшая функция|Замена|  
|--------------|------------------------|-----------------|  
|Локальные кубы|InsertInto, свойство строки подключения|Исходный синтаксис строки подключения для заполнения локальных кубов заменяется на инструкцию создания глобального куба. Дополнительные сведения см. в разделе [инструкция CREATE глобального КУБА &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-create-global-cube).|  
|Локальные кубы|CreateCube, свойство строки подключения|Исходный синтаксис строки подключения для заполнения локальных кубов заменяется на инструкцию создания глобального куба. Дополнительные сведения см. в разделе [инструкция CREATE глобального КУБА &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-create-global-cube).|  
|Интеллектуальный анализ данных|SQL Server 2000 PMML|Компонент SQL Server 2000 PMML создавал форму PMML, содержащую расширения для поддержки уникальных возможностей, предоставляемых алгоритмами интеллектуального анализа данных, недоступными в спецификации PMML. В SQL Server 2005 службы Analysis Services обновили компонент PMML до нового стандарта PMML 2.1. В результате частные расширения, добавленные в SQL Server 2000, больше не нужны, несмотря на то что они по-прежнему поддерживаются в этом выпуске.|  
|Инструкция многомерных выражений|Инструкция Create Action|Данная инструкция включена для обеспечения обратной совместимости. Заменена объектом Action. Дополнительные сведения о том, как создавать действия в последних версиях [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], см. в разделе [действия &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).|  
  
## <a name="discontinued-features-in-previous-releases"></a>Неподдерживаемые функции предыдущих версий  
 Мастер миграции, использовавшийся для переноса баз данных SQL Server 2000 Analysis Services в новые версии, более не поддерживается, так как SQL Server 2000 более не поддерживается.  
  
 Библиотека объектов DSO, которая обеспечивала совместимость с базами данных SQL Server 2000 Analysis Services, также более не поддерживается и не является частью SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Analysis Services Backward Compatibility](analysis-services-backward-compatibility.md)  
  
  

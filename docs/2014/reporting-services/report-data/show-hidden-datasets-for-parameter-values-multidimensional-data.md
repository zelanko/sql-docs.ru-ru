---
title: Отображение скрытых наборов данных для значений параметра многомерных данных (построитель отчетов и службы SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 89df13eecdce33869199e0b5a8e82b0395679475
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097016"
---
# <a name="show-hidden-datasets-for-parameter-values-for-multidimensional-data-report-builder-and-ssrs"></a>Отображение скрытых наборов данных для значений параметра в многомерных данных (построитель отчетов и службы SSRS)
  Отчет может включать автоматически создаваемые наборы данных (называемые также скрытыми наборами данных), которые по умолчанию не отображаются на панели данных отчета. Эти наборы данных создаются следующими способами.  
  
-   В некоторых конструкторах запросов для многомерных баз данных можно указать поля для фильтрации в области фильтра панели запроса, и выбрать, создавать ли параметр запроса для фильтра. Если выбран режим параметров, наборы данных отчета создаются автоматически, чтобы предоставлять допустимые значения для параметра отчета.  
  
-   При импортировании запроса, основанного на многомерных базах данных, в отчет можно также включить скрытые наборы данных.  
  
 Скрытые наборы данных недоступны для использования из мастера.  
  
 Можно сменить представление в области данных отчета, чтобы отображать в отчете все наборы данных.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a>Отображение скрытых наборов данных  
  
-   В области данных отчета щелкните правой кнопкой мыши "Наборы данных" и выберите **Показать скрытые наборы данных**.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы запросов (построитель отчетов)](../query-designers-report-builder.md)   
 [Конструкторы запросов служб Reporting Services](../reporting-services-query-designers.md)   
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Добавление данных в отчет &#40;отчетов построителя отчетов и службы SSRS&#41;](report-datasets-ssrs.md)  
  
  
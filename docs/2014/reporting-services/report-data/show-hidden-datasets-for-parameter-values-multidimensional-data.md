---
title: Отображение скрытых наборов данных для значений параметра в многомерных данных (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 50da5a57968a7304c206f2aceb2efc24239600b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224684"
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
 [Добавление данных в отчет &#40;построитель отчетов и службы SSRS&#41;](report-datasets-ssrs.md)  
  
  

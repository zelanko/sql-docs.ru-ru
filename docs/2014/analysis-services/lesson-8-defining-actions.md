---
title: 'Занятие 8: Определение действий | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab952dba40b28ed0575b6fdb8da442ea6ebeb770
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274490"
---
# <a name="lesson-8-defining-actions"></a>Занятие 8. Определение действий
  На этом занятии определяются действия в проекте служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Действие представляет собой инструкцию многомерных выражений, хранимую в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которая может быть включена в клиентские приложения и выполнена пользователем.  
  
> [!NOTE]  
>  Завершенные проекты для всех занятий в этом учебнике доступны через Интернет. Можно перейти вперед к любому занятию, используя в качестве отправной точки завершенный проект из предыдущего урока. [Щелкните здесь](http://go.microsoft.com/fwlink/?LinkID=221866) для загрузки образцов проектов, прилагаемых к этому учебнику.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают типы операций, описанные в таблице ниже.  
  
|||  
|-|-|  
|Командная строка|Выполняет команду в командной строке|  
|Dataset|Возвращает клиентскому приложению набор данных.|  
|Детализация|Возвращает инструкцию детализации в качестве выражения, которое клиент выполняет, чтобы вернуть набор строк|  
|Html|Выполняет HTML-скрипт в браузере Интернета.|  
|Частный|Выполняет операцию с использованием интерфейса, отличного от приведенных в данной таблице.|  
|Отчет|Направляет серверу отчетов параметризованный запрос на основе URL-адресов и возвращает клиентскому приложению отчет.|  
|Набор строк|Возвращает клиентскому приложению набор строк.|  
|.|Выполняет команду OLE DB.|  
|URL-адрес|Отображает динамическую веб-страницу в браузереБраузер Интернета.|  
  
 Действия позволяют пользователям запускать приложение или выполнять другие шаги в контексте выбранного элемента. Дополнительные сведения см. в разделе [Действия (службы Analysis Services — многомерные данные)](multidimensional-models/actions-analysis-services-multidimensional-data.md), [Действия в многомерных моделях](multidimensional-models/actions-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Примеры действий см. на вкладке «Шаблоны» на панели «Средства вычисления» и в примерах, содержащихся в образце хранилища данных [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW. Дополнительные сведения об установке этой базы данных см. в разделе [Установка образцов данных и проектов для учебника по многомерному моделированию в службах Analysis Services](install-sample-data-and-projects.md).  
  
 Это занятие содержит следующую задачу:  
  
 [Определение и использование действия детализации](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
 В этой задаче предстоит создать, использовать и затем изменить действие детализации связи измерений фактов, определенного ранее в этом учебнике.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 9. Определение перспектив и преобразований](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>См. также  
 [Сценарий учебника по службам Analysis Services](analysis-services-tutorial-scenario.md)   
 [Многомерное моделирование &#40;руководством по Adventure Works&#41;](multidimensional-modeling-adventure-works-tutorial.md)   
 [Действия &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)   
 [Действия в многомерных моделях](multidimensional-models/actions-in-multidimensional-models.md)  
  
  

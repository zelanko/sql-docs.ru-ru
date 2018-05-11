---
title: 'Занятие 8: Определение действий | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d1d687faa7c71e41444d258968779aa2366a31b6
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-8-defining-actions"></a>Занятие 8. Определение действий
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

На этом занятии определяются действия в проекте служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Действие представляет собой инструкцию многомерных выражений, хранимую в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которая может быть включена в клиентские приложения и выполнена пользователем.  
  
> [!NOTE]  
> Завершенные проекты для всех занятий в этом учебнике доступны через Интернет. Можно перейти вперед к любому занятию, используя в качестве отправной точки завершенный проект из предыдущего урока. [Щелкните здесь](http://go.microsoft.com/fwlink/?LinkID=221866) для загрузки образцов проектов, прилагаемых к этому учебнику.  
  
Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают типы операций, описанные в следующей таблице.  
  
|||  
|-|-|  
|Командная строка|Выполняет команду в командной строке|  
|Набор данных|Возвращает клиентскому приложению набор данных.|  
|Детализация|Возвращает инструкцию детализации в качестве выражения, которое клиент выполняет, чтобы вернуть набор строк|  
|Html|Выполняет HTML-скрипт в браузере Интернета.|  
|Частный|Выполняет операцию с использованием интерфейса, отличного от приведенных в данной таблице.|  
|Отчет|Направляет серверу отчетов параметризованный запрос на основе URL-адресов и возвращает клиентскому приложению отчет.|  
|Набор строк|Возвращает клиентскому приложению набор строк.|  
|.|Выполняет команду OLE DB.|  
|URL-адрес|Отображает динамическую веб-страницу в браузереБраузер Интернета.|  
  
Действия позволяют пользователям запускать приложение или выполнять другие шаги в контексте выбранного элемента. Дополнительные сведения см. в разделе [Действия (службы Analysis Services — многомерные данные)](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md), [Действия в многомерных моделях](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md).  
  
> [!NOTE]  
> Примеры действий см. на вкладке «Шаблоны» на панели «Средства вычисления» и в примерах, содержащихся в образце хранилища данных [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW. Дополнительные сведения об установке этой базы данных см. в разделе [Установка образцов данных и проектов для учебника по многомерному моделированию в службах Analysis Services](../analysis-services/install-sample-data-and-projects.md).  
  
Это занятие содержит следующую задачу:  
  
[Определение и использование действия детализации](../analysis-services/lesson-8-1-defining-and-using-a-drillthrough-action.md)  
В этой задаче предстоит создать, использовать и затем изменить действие детализации связи измерений фактов, определенного ранее в этом учебнике.  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 9: Определение перспектив и переводов](../analysis-services/lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>См. также  
[Сценарий учебника по службам Analysis Services](../analysis-services/analysis-services-tutorial-scenario.md)  
[Многомерное моделирование (учебник по Adventure Works)](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[Действия & #40; Analysis Services — многомерные данные & #41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)  
[Действия в многомерных моделях](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
  
  

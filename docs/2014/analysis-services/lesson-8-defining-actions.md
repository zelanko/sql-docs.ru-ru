---
title: Занятие 8. Определение действий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8293bb8d1f0465d09b296cbd18702b569f073766
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078230"
---
# <a name="lesson-8-defining-actions"></a>Занятие 8. Определение действий
  На этом занятии определяются действия в проекте служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Действие представляет собой инструкцию многомерных выражений, хранимую в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которая может быть включена в клиентские приложения и выполнена пользователем.  
  
> [!NOTE]  
>  Завершенные проекты для всех занятий в этом учебнике доступны через Интернет. Можно перейти вперед к любому занятию, используя в качестве отправной точки завершенный проект из предыдущего урока. [Щелкните здесь](https://go.microsoft.com/fwlink/?LinkID=221866) , чтобы скачать примеры проектов, которые можно найти в этом руководстве.  
  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают типы операций, описанные в таблице ниже.  
  
|||  
|-|-|  
|Командная строка|Выполняет команду в командной строке|  
|Dataset|Возвращает клиентскому приложению набор данных.|  
|Детализация|Возвращает инструкцию детализации в качестве выражения, которое клиент выполняет, чтобы вернуть набор строк|  
|Html|Выполняет HTML-скрипт в браузере Интернета.|  
|Частный|Выполняет операцию с использованием интерфейса, отличного от приведенных в данной таблице.|  
|Report|Направляет серверу отчетов параметризованный запрос на основе URL-адресов и возвращает клиентскому приложению отчет.|  
|Набор строк|Возвращает клиентскому приложению набор строк.|  
|Инструкция|Выполняет команду OLE DB.|  
|URL-адрес|Отображает динамическую веб-страницу в браузереБраузер Интернета.|  
  
 Действия позволяют пользователям запускать приложение или выполнять другие шаги в контексте выбранного элемента. Дополнительные сведения см. в разделе [Действия (службы Analysis Services — многомерные данные)](multidimensional-models/actions-analysis-services-multidimensional-data.md), [Действия в многомерных моделях](multidimensional-models/actions-in-multidimensional-models.md)  
  
> [!NOTE]  
>  Примеры действий см. на вкладке «Шаблоны» на панели «Средства вычисления» и в примерах, содержащихся в образце хранилища данных [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW. Дополнительные сведения об установке этой базы данных см. в разделе [Установка образцов данных и проектов для учебника по многомерному моделированию в службах Analysis Services](install-sample-data-and-projects.md).  
  
 Это занятие содержит следующую задачу:  
  
 [Определение и использование действия детализации](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
 В этой задаче предстоит создать, использовать и затем изменить действие детализации связи измерений фактов, определенного ранее в этом учебнике.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 9. Определение перспектив и переводов](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>См. также:  
 [Analysis Services сценарий учебника](analysis-services-tutorial-scenario.md)   
 [&#40;учебника по Adventure Works в многомерном моделировании&#41;](multidimensional-modeling-adventure-works-tutorial.md)   
 [Действия &#40;Analysis Services многомерных данных&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)   
 [Действия в многомерных моделях](multidimensional-models/actions-in-multidimensional-models.md)  
  
  

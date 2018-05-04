---
title: Изменение и удаление секций (Analysis Services — многомерные) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bce863b8acae9d6791a7b8b5e952af80fc154053
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="edit-or-delete-partitions-analyisis-services---multidimensional"></a>Изменение и удаление секций (Analysis Services — многомерные данные)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Секции куба редактируются с помощью вкладки **Секции** в конструкторе кубов в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. На вкладке **Секции** перечислены секции для всех групп мер в кубе. А также секции обратной записи с включенной функцией обратной записи.  
  
 Чтобы изменить секции для любой группы мер, разверните группу мер на вкладке **Секции** . Секции группы мер указываются в списке, основанном на их порядковых номерах, в формате таблицы; перечисленные столбцы см. в следующей таблице.  
  
 Настройки связанной группы мер необходимо редактировать в исходном кубе.  
  
 Удаление секций производится автоматически при слиянии исходной секции с целевой. Секция, указанная как источник, после успешного слияния удаляется. Также можно вручную удалить секции в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или на вкладке «Секции» в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Щелкните правой кнопкой мыши и выберите команду **Удалить**. Помните, что при удалении секции также удаляются данные и агрегирования. В качестве меры предосторожности обязательно создайте резервную копию базы данных на тот случай, что понадобится отменить данное действие.  
  
> [!NOTE]  
>  Также можно использовать XMLA-скрипты, автоматизирующие задачи по построению, слиянию и удалению секций. XMLA-скрипт может быть создан и выполнен в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]или в пользовательских SSIS-пакетах, выполняемых как задача по расписанию. Дополнительные сведения см. в статье [Автоматизация административных задач служб Analysis Services с помощью служб SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="partition-source"></a>Источник секции  
 Указывает исходную таблицу или именованный запрос для секции. Чтобы изменить исходную таблицу, щелкните ячейку, а затем нажмите кнопку обзора (**...**).  
  
 ![Исходный столбец на панели секции](../../analysis-services/multidimensional-models/media/ssas-partitionsource.png "исходный столбец на панели секции")  
  
 Если секция основывается на запросе, нажмите кнопку обзора (**...**), чтобы изменить запрос. Это изменит свойство **Source** секции. Дополнительные сведения см. в статье [Смена источника секции на другую таблицу фактов](../../analysis-services/multidimensional-models/change-a-partition-source-to-use-a-different-fact-table.md).  
  
 Можно указать таблицу в представлении источника данных, которая имеет такую же структуру, как исходная таблица источника (во внешнем источнике данных, из которого извлекаются данные). Источник может быть в любом из источников данных или представлений источников данных базы данных куба.  
  
## <a name="storage-settings"></a>Параметры хранилища  
 В конструкторе кубов на вкладке секций можно щелкнуть **Параметры хранилища** , чтобы выбрать одну из стандартных настроек для реляционного хранилища ROLAP, гибридного HOLAP или многомерного MOLAP или установить пользовательские настройки для режима хранилища и упреждающего кэширования. По умолчанию используется хранилище MOLAP, поскольку оно обеспечивает наилучшую производительность запросов. Дополнительные сведения о каждом параметре см. в разделе [Определение хранилища секции (Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models/set-partition-storage-analysis-services-multidimensional.md).  
  
 Хранилище можно настроить отдельно для каждой секции каждой группы мер в кубе. Также можно установить настройки хранилища по умолчанию для куба или группы мер. Хранилище настраивается на вкладке **Секции** мастера кубов.  
  
## <a name="see-also"></a>См. также  
 [Создание и управление локальной секции & #40; Службы Analysis Services & #41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)   
 [Проектирование агрегатов & #40; Службы Analysis Services — многомерные & #41;](../../analysis-services/multidimensional-models/designing-aggregations-analysis-services-multidimensional.md)   
 [Слияние секций в службы Analysis Services & #40; Службы SSAS — многомерные & #41;](../../analysis-services/multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  

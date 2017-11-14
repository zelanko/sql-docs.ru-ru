---
title: "Включить режим DirectQuery в SSDT | Документы Microsoft"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f3a5cfe3f2b39f35d2b2e70dd44ec11adeebcd0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="enable-directquery-mode-in-ssdt"></a>Включение режима DirectQuery в SSDT

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

В этом разделе описывается включение режима DirectQuery для проекта табличной модели в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
При включении режима DirectQuery для табличной модели, разрабатываемой в SSDT:
-   Отключаются компоненты, не совместимые с режимом DirectQuery.  
-   Проверяется существующая модель. Если компоненты не совместимы с режимом DirectQuery, отображаются предупреждения.  
-   Если перед включением режима DirectQuery импортировались данные, кэш рабочей машины опустошается.  
  
### <a name="enable-directquery"></a>Включение режима DirectQuery  
  
В SSDT на панели **Свойства** для файла **Model.bim** измените значение свойства **Режим DirectQuery**на **Включен**.  

![Включение режима DirectQuery в SSDT](../../analysis-services/tabular-models/media/enable-directquery-mode-in-ssdt.png)
  
Если в вашей модели уже установлена связь с источником данных и существующими данными, появится запрос на ввод учетных данных базы данных для подключения к реляционной базе данных. Любые данные, которые уже существуют в модели, будут удалены из кэша памяти.  
  
Если до включения режима DirectQuery ваша модель уже была частично или полностью завершена, могут возникнуть ошибки, связанные с несовместимыми функциями. В этом случае в Visual Studio откройте **список ошибок** и устраните проблемы, мешающие перевести модель в режим DirectQuery.  


### <a name="whats-next"></a>Дальнейшие действия 
Теперь с помощью мастера импорта таблиц можно импортировать данные и получить метаданные для этой модели. В качестве основы для модели вы получите таблицы, столбцы и связи данных (но не строки). 

Кроме того, чтобы проверить модель при ее создании, можно создать демонстрационную секцию для каждой таблицы и добавить в нее демонстрационные данные. Все добавленные данные используются в средстве **Анализ для Excel** или в других клиентских средствах, которые могут подключаться к базе данных рабочей области. Дополнительные сведения см. в разделе [Добавление демонстрационных данных в модель DirectQuery в режиме конструктора](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) .  
  
> [!TIP]  
    >  Даже если модель пуста, в режиме DirectQuery для каждой таблицы всегда можно посмотреть небольшой встроенный набор строк. В [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]выберите меню **Таблица** > **Свойства таблицы** , чтобы просмотреть набор данных из 50 строк.  
  
  
## <a name="see-also"></a>См. также:  
[Включение режима DirectQuery в SSMS](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[Добавление демонстрационных данных в модель DirectQuery в режиме конструктора](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  


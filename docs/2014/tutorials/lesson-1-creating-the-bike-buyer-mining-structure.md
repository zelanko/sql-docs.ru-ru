---
title: Урок 1. Создание структуры интеллектуального анализа данных для покупателя велосипеда | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025805"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>Урок 1. Создание структуры интеллектуального анализа данных для покупателя велосипеда
  На этом занятии вы создадите структуры интеллектуального анализа данных, которая позволяет предсказать, купит ли потенциальный клиент [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] велосипед. Если вы не знакомы со структурами интеллектуального анализа данных и их роли в интеллектуальном анализе данных, см. в разделе [структур интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Структуры интеллектуального анализа «Покупатель велосипеда», созданной на этом занятии, поддерживает добавление моделей интеллектуального анализа данных, на основе [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md). На следующих занятиях вы будете использовать кластерные модели интеллектуального анализа данных для исследования других способов группирования клиентов и будете использовать модели интеллектуального анализа данных дерева решений для предсказания, купит ли потенциальный клиент велосипед.  
  
## <a name="create-mining-structure-statement"></a>Инструкция CREATE MINING STRUCTURE  
 Чтобы создать структуру интеллектуального анализа данных, используйте [CREATE MINING STRUCTURE &#40;расширений интеллектуального анализа данных&#41; ](/sql/dmx/create-mining-structure-dmx) инструкции. Код инструкции можно разбить на следующие части:  
  
-   Присвоение структуре имени.  
  
-   Определение ключевого столбца.  
  
-   Определение столбцов интеллектуального анализа данных.  
  
-   Определение необязательного набора проверочных данных.  
  
 В следующем фрагменте показан общий пример инструкции CREATE MINING STRUCTURE:  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Первая строчка кода определяет имя структуры:  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 Сведения о присвоении имени объекту в расширений интеллектуального анализа (DMX), см. в разделе [идентификаторы &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/identifiers-dmx).  
  
 Следующая строка кода определяет ключевой столбец структуры интеллектуального анализа данных, уникально определяющий сущность в исходных данных:  
  
```  
<key column>,  
```  
  
 В созданной структуре интеллектуального анализа данных идентификатор клиента, `CustomerKey`, определяет некоторую сущность в исходных данных.  
  
 В следующей строке кода определяются столбцы интеллектуального анализа, используемые моделями интеллектуального анализа, связанными со структурой интеллектуального анализа:  
  
```  
<mining structure columns>  
```  
  
 Можно воспользоваться функцией DESCRETIZE внутри \<столбцы структуры интеллектуального анализа данных > для дискретизации непрерывных столбцов, используя следующий синтаксис:  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 Дополнительные сведения о дискретизации столбцов см. в разделе [методы дискретизации &#40;интеллектуального анализа данных&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md). Дополнительные сведения о типах столбцов структуры, которые можно определить интеллектуального анализа см. в разделе [столбцы структуры интеллектуального анализа данных](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
 В последней строке кода определяется необязательная секция в структуре интеллектуального анализа данных:  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Можно определить некоторую часть данных как предназначенную для проверки моделей интеллектуального анализа данных, относящихся к этой структуре, после чего оставшиеся данные применяются для обучения моделей. По умолчанию службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] создают набор проверочных данных, который содержит 30 процентов всех данных варианта. Будет добавлена спецификация, согласно которой набор проверочных данных должен содержать 30 процентов вариантов, вплоть до максимального количества, равного 1000 вариант. Если 30 процентов вариантов меньше 1000, набор проверочных данных будет содержать это меньшее количество.  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии будут выполнены следующие задачи.  
  
-   Создание нового пустого запроса.  
  
-   Изменение запроса, чтобы создать структуру интеллектуального анализа данных.  
  
-   Выполнение запроса.  
  
## <a name="creating-the-query"></a>Создание запроса  
 На первом этапе необходимо подключиться к экземпляру служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и создать новый DMX-запрос в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Создание нового DMX-запроса в среде SQL Server Management Studio  
  
1.  Откройте [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  В **соединение с сервером** диалоговом окне для **тип сервера**выберите **служб Analysis Services**. В **имя_сервера**, тип `LocalHost`, или введите имя экземпляра [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , требуется подключение к для этого занятия. Нажмите кнопку **Соединить**.  
  
3.  В **обозревателя объектов**, щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], пункты **новый запрос**и нажмите кнопку **расширений интеллектуального анализа данных** открыть **редактора запросов**и создать новый, пустой запрос.  
  
## <a name="altering-the-query"></a>Изменение запроса  
 Следующим шагом будет изменение инструкции CREATE MINING STRUCTURE, описанной выше, чтобы создать структуру интеллектуального анализа данных для покупателя велосипеда.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>Настройка инструкции CREATE MINING STRUCTURE  
  
1.  В редакторе запросов скопируйте общий пример инструкции CREATE MINING STRUCTURE в пустое окно запроса.  
  
2.  Вместо  
  
    ```  
    [<mining structure>]   
    ```  
  
     вставьте  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  Вместо  
  
    ```  
    <key column>   
    ```  
  
     вставьте  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  Вместо  
  
    ```  
    <mining structure columns>   
    ```  
  
     вставьте  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  Вместо  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     вставьте  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     Полная инструкция создания структуры интеллектуального анализа данных должна выглядеть так:  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
7.  В **Сохранить как** диалоговом окне перейдите к соответствующей папке и присвойте файлу имя `Bike Buyer Structure.dmx`.  
  
## <a name="executing-the-query"></a>Выполнение запроса  
 На последнем шаге нужно выполнить запрос. После создания и сохранения запроса его необходимо выполнить. Это означает, что должна быть запущена инструкция для создания на сервере структуры интеллектуального анализа. Дополнительные сведения о выполнении запросов в редакторе запросов, см. в разделе [редактор запросов ядра СУБД &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Выполнение запроса  
  
1.  В редакторе запросов на панели инструментов щелкните **Execute**.  
  
     Состояние запроса **сообщений** вкладку в нижней части редактора запросов после завершения выполнения инструкции. Сообщение должно выглядеть следующим образом:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Новая структура с именем **Bike Buyer** теперь существует на сервере.  
  
 На следующем занятии вы добавите модели интеллектуального анализа данных в только что созданную структуру.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 2. Добавление моделей интеллектуального анализа данных для структуры интеллектуального анализа данных для покупателя велосипеда](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  

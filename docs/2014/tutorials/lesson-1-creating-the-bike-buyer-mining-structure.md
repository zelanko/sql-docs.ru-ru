---
title: Занятие 1. Создание структуры интеллектуального анализа данных покупателя велосипеда | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62678500"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>Урок 1. Создание структуры интеллектуального анализа данных для покупателя велосипеда
  На этом занятии вы создадите структуры интеллектуального анализа данных, которая позволяет предсказать, купит ли потенциальный клиент [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] велосипед. Дополнительные сведения о структурах интеллектуального анализа данных и их ролях в интеллектуальном анализе см. в разделе [структуры интеллектуального анализа данных &#40;Analysis Services-&#41;интеллектуального анализа ](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Структура интеллектуального анализа данных покупателя велосипеда, которая будет создана на этом занятии, поддерживает добавление моделей интеллектуального анализа данных на основе алгоритма [кластеризации Майкрософт](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft для дерева принятия решений](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md). На следующих занятиях вы будете использовать кластерные модели интеллектуального анализа данных для исследования других способов группирования клиентов и будете использовать модели интеллектуального анализа данных дерева решений для предсказания, купит ли потенциальный клиент велосипед.  
  
## <a name="create-mining-structure-statement"></a>Инструкция CREATE MINING STRUCTURE  
 Чтобы создать структуру интеллектуального анализа данных, используйте инструкцию [создания структуры интеллектуального анализа данных &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) . Код инструкции можно разбить на следующие части:  
  
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
  
 Сведения об именовании объекта в расширениях интеллектуального анализа данных см. в разделе [идентификаторы &#40;dmx&#41;](/sql/dmx/identifiers-dmx).  
  
 Следующая строка кода определяет ключевой столбец структуры интеллектуального анализа данных, уникально определяющий сущность в исходных данных:  
  
```  
<key column>,  
```  
  
 В созданной структуре интеллектуального анализа данных идентификатор клиента, `CustomerKey`, определяет некоторую сущность в исходных данных.  
  
 В следующей строке кода определяются столбцы интеллектуального анализа, используемые моделями интеллектуального анализа, связанными со структурой интеллектуального анализа:  
  
```  
<mining structure columns>  
```  
  
 Функцию ДИСКРЕТИЗАЦИИ можно использовать в \<столбцах структуры интеллектуального анализа данных> для дискретизации непрерывных столбцов с помощью следующего синтаксиса:  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 Дополнительные сведения о дискретизации столбцов см. в разделе [методы дискретизации &#40;&#41;интеллектуального анализа данных ](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md). Дополнительные сведения о типах столбцов структуры интеллектуального анализа данных, которые можно определить, см. в разделе [столбцы структуры интеллектуального анализа данных](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
 В последней строке кода определяется необязательная секция в структуре интеллектуального анализа данных:  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Можно определить некоторую часть данных как предназначенную для проверки моделей интеллектуального анализа данных, относящихся к этой структуре, после чего оставшиеся данные применяются для обучения моделей. По умолчанию службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] создают набор проверочных данных, который содержит 30 процентов всех данных варианта. Будет добавлена спецификация, согласно которой набор проверочных данных должен содержать 30 процентов вариантов, вплоть до максимального количества, равного 1000 вариант. Если 30 процентов вариантов меньше 1000, набор проверочных данных будет содержать это меньшее количество.  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии будут выполнены следующие задачи.  
  
-   Создание нового пустого запроса.  
  
-   Изменение запроса, чтобы создать структуру интеллектуального анализа данных.  
  
-   Выполните запрос.  
  
## <a name="creating-the-query"></a>Создание запроса  
 На первом этапе необходимо подключиться к экземпляру служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и создать новый DMX-запрос в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Создание нового DMX-запроса в среде SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  В диалоговом окне **соединение с сервером** в поле **тип сервера**выберите **Analysis Services**. В поле **имя сервера**введите `LocalHost`или введите имя экземпляра [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , к которому необходимо подключиться для этого занятия. Нажмите кнопку **Соединить**.  
  
3.  В **обозревателе объектов**щелкните правой [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]кнопкой мыши экземпляр, наведите указатель на пункт **создать запрос**и выберите **расширения интеллектуального анализа данных** , чтобы открыть **Редактор запросов** и новый пустой запрос.  
  
## <a name="altering-the-query"></a>Изменение запроса  
 Следующим шагом будет изменение инструкции CREATE MINING STRUCTURE, описанной выше, чтобы создать структуру интеллектуального анализа данных для покупателя велосипеда.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>Настройка инструкции CREATE MINING STRUCTURE  
  
1.  В редакторе запросов скопируйте общий пример инструкции CREATE MINING STRUCTURE в пустое окно запроса.  
  
2.  Вместо  
  
    ```  
    [<mining structure>]   
    ```  
  
     на:  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  Вместо  
  
    ```  
    <key column>   
    ```  
  
     на:  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  Вместо  
  
    ```  
    <mining structure columns>   
    ```  
  
     на:  
  
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
  
     на:  
  
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
  
7.  В диалоговом окне **Сохранить как** перейдите в соответствующую папку и присвойте файлу `Bike Buyer Structure.dmx`имя.  
  
## <a name="executing-the-query"></a>Выполнение запроса  
 На последнем шаге нужно выполнить запрос. После создания и сохранения запроса его необходимо выполнить. Это означает, что должна быть запущена инструкция для создания на сервере структуры интеллектуального анализа. Дополнительные сведения о выполнении запросов в редакторе запросов см. в разделе [ядро СУБД редактор запросов &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Выполнение запроса  
  
1.  На панели инструментов редактора запросов нажмите кнопку **выполнить**.  
  
     Состояние запроса отображается на вкладке **сообщения** в нижней части редактора запросов после завершения выполнения инструкции. Сообщение должно выглядеть следующим образом:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     На сервере теперь существует новая структура с именем **Bike Buyer** .  
  
 На следующем занятии вы добавите модели интеллектуального анализа данных в только что созданную структуру.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 2. Добавление моделей интеллектуального анализа к структуре интеллектуального анализа "Покупатель велосипеда"](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  

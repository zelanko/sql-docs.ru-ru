---
title: Занятие 3. Обработка структуры интеллектуального анализа данных покупателя велосипеда | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "62655808"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>Урок 3. Обработка структуры интеллектуального анализа данных "Покупатель велосипеда"
  На этом занятии для обработки структур и моделей интеллектуального анализа данных, созданных на занятии 1, вы будете использовать инструкцию INSERT INTO и представление vTargetMail из [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] примера. для этого нужно создать [структуру интеллектуального анализа данных для покупателя велосипеда](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) и [занятие 2](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).  
  
 При обработке структуры интеллектуального анализа данных службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] считывают исходные данные и создают структуры, поддерживающие модели интеллектуального анализа данных. При обработке модели интеллектуального анализа данных данные, определенные структурой интеллектуального анализа данных, проходят через выбранный пользователем алгоритм интеллектуального анализа данных. Алгоритм находит тренды и шаблоны и сохраняет эти данные в модели интеллектуального анализа данных. Поэтому в модели интеллектуального анализа данных содержатся не фактические исходные данные, а данные, выявленные алгоритмом. Дополнительные сведения об обработке моделей интеллектуального анализа данных см. в разделе [требования к обработке и рекомендации &#40;&#41;интеллектуального анализа ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Повторная обработка структуры интеллектуального анализа данных нужна только в том случае, когда изменяются столбцы структуры или исходные данные. При добавлении модели интеллектуального анализа данных к уже обработанной структуре интеллектуального анализа данных можно использовать инструкцию INSERT INTO MINING MODEL для обучения новой модели интеллектуального анализа данных.  
  
## <a name="train-structure-template"></a>Шаблон обучения структуры  
 Чтобы обучить структуру интеллектуального анализа данных и связанные с ней модели интеллектуального анализа данных, используйте инструкцию [INSERT в &#40;DMX&#41;](/sql/dmx/insert-into-dmx) . Код инструкции можно разбить на следующие части:  
  
-   Определение структуры интеллектуального анализа данных  
  
-   Список столбцов структуры интеллектуального анализа  
  
-   Определение обучающих данных  
  
 В следующем фрагменте показан общий пример инструкции INSERT INTO:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 В первой строчке кода задается структура интеллектуального анализа данных, которую необходимо обучить:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Следующая строка кода указывает столбцы, определенные структурой интеллектуального анализа данных. Необходимо перечислить все столбцы структуры интеллектуального анализа данных, и каждый столбец должен сопоставляться с каким-либо столбцом из данных исходного запроса.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Последней строчкой кода определяются данные, с помощью которых будет проводиться обучение структуры интеллектуального анализа данных.  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 На этом занятии требуется определить исходные данные с помощью инструкции `OPENQUERY`. Дополнительные сведения о других методах определения исходного запроса см. в разделе [&#60;Source Data query&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии требуется выполнить следующую задачу:  
  
-   Обработка структуры интеллектуального анализа данных «Покупатель велосипеда»  
  
## <a name="processing-the-predictive-mining-structure"></a>Обработка прогнозирующей структуры интеллектуального анализа данных  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>Обработка структуры интеллектуального анализа данных с помощью инструкции INSERT INTO  
  
1.  В окне **Обозреватель объектов**щелкните правой кнопкой мыши экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], укажите **Создать запрос**, а затем выберите пункт **Расширения интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте стандартный пример использования инструкции INSERT INTO в пустое окно запроса.  
  
3.  Вместо  
  
    ```  
    [<mining structure name>]   
    ```  
  
     на:  
  
    ```  
    Bike Buyer  
    ```  
  
4.  Вместо  
  
    ```  
    <mining structure columns>  
    ```  
  
     на:  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
    [Commute Distance],  
    [Education],  
    [Gender],  
    [House Owner Flag],  
    [Marital Status],  
    [Number Cars Owned],  
    [Number Children At Home],  
    [Occupation],  
    [Region],  
    [Total Children],  
    [Yearly Income]  
    ```  
  
5.  Вместо  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     на:  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     В инструкции OPENQUERY для доступа к представлению vTargetMail указан источник данных [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. В указанном представлении содержатся исходные данные, которые будут использоваться для обучения моделей интеллектуального анализа данных.  
  
     Полная инструкция теперь должна выглядеть следующим образом.  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]     
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
7.  В диалоговом окне **Сохранить как** перейдите в соответствующую папку и присвойте файлу `Process Bike Buyer Structure.dmx`имя.  
  
8.  На панели инструментов нажмите кнопку **Выполнить** .  
  
 На следующем занятии будет изучено содержимое моделей интеллектуального анализа данных, добавленных к структуре интеллектуального анализа данных на текущем занятии.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 4: Просмотр моделей интеллектуального анализа данных "Покупатель велосипеда"](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  

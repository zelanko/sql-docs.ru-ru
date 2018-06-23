---
title: 'Занятие 3: Обработка структуры интеллектуального анализа данных для покупателя велосипеда | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae7d871f4695d4109866a6a25979936116838d17
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312642"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>Занятие 3: Обработка структуры интеллектуального анализа данных для покупателя велосипеда
  На этом занятии будет использовать вставки в инструкции и представления vTargetMail из [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] образца базы данных для обработки структуры интеллектуального анализа данных и моделей интеллектуального анализа данных, созданных в [занятия 1: Создание структуры интеллектуального анализа данных Bike Buyer](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) и [уроке 2: добавление моделей интеллектуального анализа данных для структуры интеллектуального анализа данных для покупателя велосипеда](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).  
  
 При обработке структуры интеллектуального анализа данных службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] считывают исходные данные и создают структуры, поддерживающие модели интеллектуального анализа данных. При обработке модели интеллектуального анализа данных данные, определенные структурой интеллектуального анализа данных, проходят через выбранный пользователем алгоритм интеллектуального анализа данных. Алгоритм находит тренды и шаблоны и сохраняет эти данные в модели интеллектуального анализа данных. Поэтому в модели интеллектуального анализа данных содержатся не фактические исходные данные, а данные, выявленные алгоритмом. Дополнительные сведения об обработке моделей интеллектуального анализа данных см. в разделе [обработке требования и соображения &#40;интеллектуального анализа данных&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Повторная обработка структуры интеллектуального анализа данных нужна только в том случае, когда изменяются столбцы структуры или исходные данные. При добавлении модели интеллектуального анализа данных к уже обработанной структуре интеллектуального анализа данных можно использовать инструкцию INSERT INTO MINING MODEL для обучения новой модели интеллектуального анализа данных.  
  
## <a name="train-structure-template"></a>Шаблон обучения структуры  
 Для обучения структуры интеллектуального анализа данных и связанные с ней модели используется [INSERT INTO &#40;расширений интеллектуального анализа данных&#41; ](/sql/dmx/insert-into-dmx) инструкции. Код инструкции можно разбить на следующие части:  
  
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
  
 На этом занятии требуется определить исходные данные с помощью инструкции `OPENQUERY`. Сведения о других способах определения исходного запроса см. в разделе [ &#60;запросом источника данных&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии требуется выполнить следующую задачу:  
  
-   Обработка структуры интеллектуального анализа данных «Покупатель велосипеда»  
  
## <a name="processing-the-predictive-mining-structure"></a>Обработка прогнозирующей структуры интеллектуального анализа данных  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>Обработка структуры интеллектуального анализа данных с помощью инструкции INSERT INTO  
  
1.  В **обозревателя объектов**, щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], пункты **новый запрос**, а затем нажмите кнопку **расширений интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте стандартный пример использования инструкции INSERT INTO в пустое окно запроса.  
  
3.  Вместо  
  
    ```  
    [<mining structure name>]   
    ```  
  
     вставьте  
  
    ```  
    Bike Buyer  
    ```  
  
4.  Вместо  
  
    ```  
    <mining structure columns>  
    ```  
  
     вставьте  
  
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
  
     вставьте  
  
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
  
7.  В **Сохранить как** диалоговое окно, перейдите к соответствующей папке и присвойте файлу имя `Process Bike Buyer Structure.dmx`.  
  
8.  На панели инструментов нажмите кнопку **Выполнить** .  
  
 На следующем занятии будет изучено содержимое моделей интеллектуального анализа данных, добавленных к структуре интеллектуального анализа данных на текущем занятии.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 4. Просмотр моделей интеллектуального анализа данных для покупателя велосипеда](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  

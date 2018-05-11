---
title: 'Analysis Services tutorial дополнительного занятия: неоднородные иерархии | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e38e1e2b888ce92fad826fda43624e19a75c2110
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>Дополнительного занятия - неоднородные иерархии

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

В этом дополнительном занятии устранить распространенные проблемы при повороте на иерархии, которые содержат пустые значения (члены) на различных уровнях. Например организация которой менеджеры высокого уровня координируют менеджеров отделов и не менеджеров подчиненных. Или географические иерархии, состоящие из страны, региона и города, которые включают города без родительского штата или провинции, например Вашингтон о. к., Ватикан. Если пустые элементы иерархии, часто заканчиваются на разных или без выравнивания, уровни.

![AS-Lesson-Detail-ragged-hierarchies-TABLE](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

Табличные модели на уровне совместимости 1400 имеют дополнительный **скрыть элементы** свойство для иерархии. **По умолчанию** предполагается нет пустой членов на любом уровне. **Скрыть пустые элементы** позволяет исключить пустые элементы из иерархии, при добавлении в сводную таблицу или отчет.  
  
Предполагаемое время выполнения данного занятия: **20 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
В этой статье дополнительное занятие является частью учебника по табличному моделированию. Перед выполнением задач в этом дополнительном занятии, необходимо завершить все предыдущие занятия или иметь завершенный проект образце модели Интернет-продаж Adventure Works. 

При создании проекта Интернет-продаж AW в рамках учебника модели не еще содержит любые данные или неровными иерархиями. Для выполнения этого дополнительного занятия, сначала нужно создавать проблему, добавив некоторые дополнительные таблицы, связи, вычисляемые столбцы, меры и новую иерархию организации. Эта часть занимает около 15 минут. Затем вы сможете решает эту проблему в течение нескольких минут.  

## <a name="add-tables-and-objects"></a>Добавление таблиц и объектов
  
### <a name="to-add-new-tables-to-your-model"></a>Чтобы добавить новые таблицы в модель
  
1.  В табличной модели обозревателе разверните **источники данных**, щелкните правой кнопкой мыши подключение > **импорта новых таблиц**.
  
2.  Выберите в навигаторе **DimEmployee** и **FactResellerSales**, а затем нажмите кнопку **ОК**.

3.  В редакторе запросов щелкните **импорта**

4.  Создайте следующую [связи](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | Таблица 1           | Столбец       | Направление фильтра   | Таблица 2     | Столбец      | Активен |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | По умолчанию            | DimDate     | Дата        | Да    |
    | FactResellerSales | DueDate      | По умолчанию            | DimDate     | Дата        | Нет     |
    | FactResellerSales | ShipDateKey  | По умолчанию            | DimDate     | Дата        | Нет     |
    | FactResellerSales | ProductKey   | По умолчанию            | DimProduct  | ProductKey  | Да    |
    | FactResellerSales | EmployeeKey  | К обеим таблицам | DimEmployee | EmployeeKey | Да    |

5. В **DimEmployee** таблице, создайте следующую [вычисляемых столбцов](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

    **Путь** 
    ```
    =PATH([EmployeeKey],[ParentEmployeeKey])
    ```

    **Полное имя** 
    ```
    =[FirstName] & " " & [MiddleName] & " " & [LastName]
    ```

    **LEVEL1** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],1,1)) 
    ```

    **Level2** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],2,1)) 
    ```

    **Level3** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],3,1)) 
    ```

    **Level4** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],4,1)) 
    ```

    **Уровень 5** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],5,1)) 
    ```

6.  В **DimEmployee** , куда вводится [иерархии](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md) с именем **организации**. Добавьте следующие столбцы в порядке: **Level1**, **Level2**, **Level3**, **Level4**, **уровень 5**.

7.  В **FactResellerSales** таблице, создайте следующую [мер](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  Используйте [анализ в Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md) для открытия Excel и автоматического создания сводной таблицы.

9.  В **полей сводной таблицы**, добавьте **организации** иерархии из **DimEmployee** таблицы, к **строк**и  **ResellerTotalSales** относительно **FactResellerSales** таблицы, к **значения**.

    ![AS-Lesson-Detail-ragged-hierarchies-PivotTable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    Как видно в сводной таблице, иерархии отображаются строки, которые остаются неровными. Существует множество строк, в которой отображаются пустые элементы.

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>Чтобы устранить ошибку неровной иерархии, члены скрыть свойства

1.  В **обозреватель табличной модели**, разверните **таблиц** > **DimEmployee** > **иерархий**  >  **Организации**.

2.  В **свойства** > **скрыть элементы**выберите **скрыть пустые элементы**. 

    ![AS-Lesson-Detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  В Excel обновите сводную таблицу. 

    ![AS-Lesson-Detail-ragged-hierarchies-PivotTable-Refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    Теперь все выглядит гораздо лучше!

## <a name="see-also"></a>См. также   
[Урок 9. Создание иерархий](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[Дополнительного занятия - динамической безопасности](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Дополнительного занятия - строки детализации](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  

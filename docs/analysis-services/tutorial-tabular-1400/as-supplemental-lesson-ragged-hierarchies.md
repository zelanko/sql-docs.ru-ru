---
title: 'Дополнительное занятие для учебника по Analysis Services: неоднородные иерархии | Документация Майкрософт'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc5a2164576e2e6142d8835dad6f6c114b7a9c5b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042308"
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>Дополнительное занятие. неоднородные иерархии

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

В этом дополнительном занятии вы устраните распространенную проблему при сведении иерархий, которые содержат пустые значения (члены) на разных уровнях. Например организация где имеет руководителя, руководителей отделов и не менеджеров непосредственных подчиненных. Или географические иерархии, состоящие из страны, региона и города, которые включают города без родительского штат или провинцию, например Вашингтон о, Ватикан. Когда иерархия содержит пустые члены, она часто опускается на другие — или неоднородные — уровни.

![AS-Lesson-Detail-ragged-hierarchies-TABLE](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

Табличные модели с уровнем совместимости 1400 имеют дополнительное **скрыть члены** свойство для иерархий. **По умолчанию** предполагает отсутствие пустых членов на любом уровне. **Скрыть пустые члены** исключает пустые члены из иерархии при добавлении в сводную таблицу или отчет.  
  
Предполагаемое время выполнения данного занятия: **20 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
В этой статье дополнительное занятие входит в учебник по табличному моделированию. Перед выполнением задач в этом дополнительном занятии, необходимо завершить все предыдущие занятия или иметь завершенный проект образца модели Adventure Works Internet Sales. 

Если в рамках этого руководства вы создали проект AW Internet Sales, модель не еще содержит данные или неоднородные иерархии. Для выполнения этого дополнительного занятия, необходимо сначала создать проблему, добавив несколько дополнительных таблиц, создать связи, вычисляемые столбцы, меры и новую иерархию организации. Эта часть займет около 15 минут. Затем вам потребуется решить проблему за несколько минут.  

## <a name="add-tables-and-objects"></a>Добавление таблиц и объектов
  
### <a name="to-add-new-tables-to-your-model"></a>Чтобы добавить новые таблицы в модель
  
1.  В обозревателе табличных моделей разверните **источников данных**, щелкните правой кнопкой мыши подключение > **импортировать новые таблицы**.
  
2.  В навигаторе выберите **DimEmployee** и **FactResellerSales**, а затем нажмите кнопку **ОК**.

3.  В редакторе запросов щелкните **импорта**

4.  Создайте следующую [связи](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | Таблица 1           | Столбец       | Направление фильтра   | Таблица 2     | Столбец      | Активен |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | По умолчанию            | DimDate     | Дата        | Да    |
    | FactResellerSales | DueDate      | По умолчанию            | DimDate     | Дата        | Нет     |
    | FactResellerSales | ShipDateKey  | По умолчанию            | DimDate     | Дата        | Нет     |
    | FactResellerSales | ProductKey   | По умолчанию            | DimProduct  | ProductKey  | Да    |
    | FactResellerSales | EmployeeKey  | К обеим таблицам | DimEmployee | EmployeeKey | Да    |

5. В **DimEmployee** таблицы, создайте следующую [вычисляемых столбцов](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

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

6.  В **DimEmployee** таблицы, создайте [иерархии](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md) с именем **организации**. Добавьте следующие столбцы по порядку: **Level1**, **Level2**, **Level3**, **Level4**, **Level5**.

7.  В **FactResellerSales** таблицы, создайте следующую [мер](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  Используйте [анализ в Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md) открыть Excel и автоматически создать сводную таблицу.

9.  В **поля сводной таблицы**, добавьте **организации** иерархии из **DimEmployee** таблицы **строк**и  **ResellerTotalSales** меру **FactResellerSales** таблицы **значения**.

    ![AS-Lesson-Detail-ragged-hierarchies-PivotTable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    Как можно видеть в сводной таблице, иерархия отображает неоднородные строки. Имеется много строк, в которой отображаются пустые члены.

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>Чтобы исправление неоднородной иерархии путем установки свойства скрыть члены

1.  В **обозреватель табличных моделей**, разверните **таблиц** > **DimEmployee** > **иерархий**  >  **Организации**.

2.  В **свойства** > **скрыть члены**выберите **скрыть пустые члены**. 

    ![AS-Lesson-Detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  Вернитесь в Excel обновите сводную таблицу. 

    ![AS-Lesson-Detail-ragged-hierarchies-PivotTable-Refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    Теперь выглядит гораздо лучше!

## <a name="see-also"></a>См. также   
[Урок 9. Создание иерархий](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[Дополнительное занятие. динамическая безопасность](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Дополнительное занятие. строки детализации](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  

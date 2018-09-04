---
title: Учебник. Общие сведения о выражениях | Документация Майкрософт
ms.date: 09/16/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.suite: pro-bi
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 64fbdea1fd5f80453daeb4541b16cb63292cbf4c
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43268677"
---
# <a name="tutorial-introducing-expressions"></a>Учебник. Общие сведения о выражениях
В этом учебнике по [!INCLUDE[ssRBnoversion_md](../includes/ssrbnoversion.md)] вы научитесь использовать выражения со стандартными функциями и операторами для создания эффективных и гибких отчетов [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] с разбивкой на страницы. 

Вы будете создавать выражения, производящие объединение значений имен, поиск значений в отдельном наборе данных, отображающие различные цвета в зависимости от значений полей, и т. д.  
  
В отчете чередуются строки белого и другого цвета. В отчет включен параметр для выбора цвета строк, отличных от белых.  
  
На этом рисунке показан отчет, похожий на тот, который будет в итоге создан.  
  
![руководство-по-выражениям-построителя-отчетов-в-браузере](../reporting-services/media/report-builder-expression-tutorial-in-browser.png) 
  
Предполагаемое время для выполнения заданий данного учебника: 30 минут.  
  
## <a name="requirements"></a>Требования  
Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/prerequisites-for-tutorials-report-builder.md).  
  
## <a name="Setup"></a>1. Создание табличного отчета и набора данных с помощью мастера таблицы или матрицы  
В этом разделе вы создадите табличный отчет, источник данных и набор данных. При создании макета таблицы будут включены лишь несколько полей. После завершения работы мастера добавьте столбцы вручную. Мастер позволяет легко структурировать таблицу.  
  
> [!NOTE]  
> В этом учебнике запрос уже содержит значения данных, поэтому внешний источник данных не требуется. В связи с этим запрос получается весьма длинным. В рабочей среде запрос не будет содержать данные. Этот запрос содержит данные только в учебных целях.  
  
### <a name="to-create-a-table-report"></a>Создание табличного отчета  
  
1.  [Запустите построитель отчетов](../reporting-services/report-builder/start-report-builder.md) с компьютера, веб-портала [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] или сервера в режиме интеграции с SharePoint.  
  
    Откроется диалоговое окно **Создать отчет или набор данных** .  
  
    Если диалоговое окно **Новый отчет или набор данных** не появилось, в меню **Файл** выберите команду **Создать**.  
  
2.  Убедитесь, что на левой панели выбран **Новый отчет** .  
  
3.  На панели справа выберите **Мастер таблицы или матрицы**.  
  
4.  На странице **Выбор набора данных** выберите **Создать набор данных** > **Далее**.  
  
6.  На странице **Выбор соединения с источником данных** выберите источник данных, имеющий тип **SQL Server**. Выберите источник данных из списка или перейдите на сервер отчетов, чтобы выбрать его там.  

    > [!NOTE]  
    > При наличии необходимых разрешений не имеет существенного значения, какой источник данных вы выбираете. Этот источник данных не будет использоваться для получения данных. Дополнительные сведения см. в разделе [Альтернативные способы создания подключения к данным &#40;построитель отчетов&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
7.  Нажмите кнопку **Далее**.  
  
8.  На странице **Проектирование запроса** нажмите кнопку **Изменить как текст**.  
  
9. На панель запроса вставьте следующий запрос:  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Female' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2015-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2015-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2015-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2015-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2015-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2015-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2015-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2015-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2015-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2015-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2015-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2015-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2015-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2015-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2015-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2015-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2015-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2015-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2015-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2015-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2015-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2015-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2015-11-30' AS date) AS LastPurchase  
    ```  

  
10. На панели инструментов конструктора запросов нажмите кнопку **Выполнить** (**!**). В результирующем наборе будет 23 строки данных в следующих столбцах: FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase и LastPurchase.  

    ![руководство-по-выражениям-построителя-отчетов-запрос-как-текст](../reporting-services/media/report-builder-expression-tutorial-query-as-text.png)
  
11. Нажмите кнопку **Далее**.  
  
12. На странице **Размещение полей** перетащите следующие поля в указанном порядке из списка **Доступные поля** в список **Значения** .  
  
    -   StateProvince   
    -   CountryRegionID  
    -   LastPurchase  
    -   YTDPurchase  
  
    Поскольку столбцы CountryRegionID и YTDPurchase содержат числовые данные, по умолчанию к ним применяется статистическое выражение SUM, но суммировать их не нужно.  
   
13. В списке **Значения** щелкните правой кнопкой мыши поле **CountryRegionID** и снимите флажок **Сумма** .  
  
    Суммирование больше не применяется к полю CountryRegionID.  
  
14. В списке **Значения** щелкните правой кнопкой мыши **YTDPurchase** и выберите пункт **Сумма** .  
  
    Суммирование больше не применяется к полю YTDPurchase.  
    
    ![руководство-по-выражениям-построителя-отчетов-без-суммы](../reporting-services/media/report-builder-expression-not-sum.png)
  
15. Нажмите кнопку **Далее**.  
  
16. На странице **Выбор макета** оставьте параметры по умолчанию и нажмите кнопку **Далее**.  

    ![руководство-по-выражениям-построителя-отчетов-выбор-макета](../reporting-services/media/report-builder-expression-tutorial-choose-layout.png)
  
17. Нажмите кнопку **Готово**.  
  
## <a name="UpdateNames"></a>2. Обновление имен по умолчанию для источника и набора данных  
  
### <a name="to-update-the-default-name-of-the-data-source"></a>Изменение имени источника данных по умолчанию  
  
1.  В области данных отчета разверните папку **Источники данных** .  
  
2.  Щелкните правой кнопкой мыши пункт **DataSource1** и выберите пункт **Свойства источника данных**.  
  
3.  В поле **Имя** введите **ExpressionsDataSource**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-update-the-default-name-of-the-dataset"></a>Изменение имени набора данных по умолчанию  
  
1.  В области данных отчета разверните папку **Наборы данных** .  
  
2.  Щелкните правой кнопкой мыши пункт **DataSet1** и выберите пункт **Свойства набора данных**.  

    ![руководство-по-выражениям-построителя-отчетов-переименование-набора-данных](../reporting-services/media/report-builder-expression-tutorial-rename-dataset.png)
  
3.  В поле **Имя** введите **Expressions**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="Concatenate"></a>3. Отображение фамилии и инициала имени  
В этом разделе в выражении используется функция **Left** и оператор **Concatenate** (**&**) для вычисления имени, состоящего из фамилии и инициала имени. Можно построить выражение в пошаговом режиме либо пропустить процедуру, а затем скопировать и вставить выражение из учебника в диалоговом окне **Выражение** .   
  
1.  Щелкните правой кнопкой мыши столбец **StateProvince** , наведите указатель на пункт **Вставить столбец**, а затем выберите пункт **Слева**.  
  
    Новый столбец будет добавлен слева от столбца **StateProvince** . 
    
    ![руководство-по-выражениям-построителя-отчетов-вставка-столбца](../reporting-services/media/report-builder-expression-tutorial-insert-column.png) 
  
2.  Щелкните заголовок нового столбца и введите **Name**.  
  
3.  Щелкните правой кнопкой мыши ячейку данных для столбца **Name** и выберите пункт **Выражение**.  

    ![руководство-по-выражениям-построителя-отчетов-вставка-выражения](../reporting-services/media/report-builder-expression-tutorial-insert-expression.png)
  
4.  В диалоговом окне **Выражение** разверните узел **Общие функции**и выберите **Текст**.  
  
5.  В списке **Элемент** дважды щелкните **Left**.  
  
    В выражение будет добавлена функция **Left** .  
    
    ![руководство-по-выражениям-построителя-отчетов-функция-left](../reporting-services/media/report-builder-expression-tutorial-left-function.png)
  
6.  В списке **Категория** щелкните **Поля (выражения)**.  
  
7.  В списке **Значения** дважды щелкните **FirstName**.  
  
8.  Введите **, 1)**  
  
    Это выражение извлекает один символ из значения **FirstName** , считая слева.  
  
9. Введите **&". "&**  

    В конец выражения будут добавлены точка и пробел.
  
10. В списке **Значения** дважды щелкните **LastName**.  
  
    Законченное выражение выглядит следующим образом: `=Left(Fields!FirstName.Value, 1) &". "& Fields!LastName.Value`  
    
    ![руководство-по-выражениям-построителя-отчетов-законченное-выражение](../reporting-services/media/report-builder-expression-tutorial-complete-name-expression.png)
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  

## <a name="DateFormat"></a>(Необязательно.) Форматирование столбцов даты и валюты и строки заголовков  
В этом разделе вы отформатируете столбец **LastPurchase** , содержащий даты, и столбец YTDPurchase, содержащий валюту. Вы также зададите необходимый формат для строки заголовков.  
  
### <a name="to-format-the-date-column"></a>Форматирование столбца дат  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Выберите ячейку данных в столбце **LastPurchase** и на вкладке **Главная** в разделе **Число** выберите **Дата**.  

    ![руководство-по-выражениям-построителя-отчетов-формат-дат](../reporting-services/media/report-builder-expression-tutorial-date-format.png)
  
3.  В разделе **Число** щелкните стрелку рядом с полем **Стили заполнителя** и выберите **Образцы значений**. 

    ![руководство-по-выражениям-построителя-отчетов-образцы-значений](../reporting-services/media/report-builder-expression-tutorial-sample-values.png)

    Вы увидите пример выбранного форматирования. 
  
### <a name="to-format-the-currency-column"></a>Форматирование столбца валют

- Выберите ячейку данных в столбце **YTDPurchase** и в разделе **Число** выберите **Символ валюты**.
 
### <a name="to-format-the-column-headers"></a>Форматирование заголовков столбцов

1. Выберите строку заголовков столбцов.

2. На вкладке **Главная** в разделе **Абзац** выберите **Слева**. 

    ![руководство-по-выражениям-построителя-отчетов-форматирование-заголовков](../reporting-services/media/report-builder-expression-tutorial-format-headings.png)

3. Нажмите кнопку **Выполнить** для предварительного просмотра отчета. 

Вот как на данный момент выглядит отчет с отформатированными заголовками столбцов, датами и валютами.

![руководство-по-выражениям-построителя-отчетов-предпросмотр-форматирования](../reporting-services/media/report-builder-expression-tutorial-preview-formatted.png)

  
## <a name="Gender"></a>4. Обозначение пола цветом  
В этом разделе вы добавите цвет для обозначения пола человека. Вы добавите новый столбец для отображения цвета, а затем определите цвет, который будет отображаться в столбце исходя из значения поля Gender.  
  
Чтобы сохранить цвет, примененный к конкретной ячейке таблицы при преобразовании отчета в отчет с чередованием, будет добавлен прямоугольник, а затем для него будет добавлен цвет фона.  
    
 
### <a name="to-add-an-mf-column"></a>Добавление столбца пола  
  
1.  Щелкните правой кнопкой мыши столбец **Name** , наведите указатель на пункт **Вставить столбец**, а затем выберите пункт **Слева**.  
  
    Новый столбец будет добавлен слева от столбца **Name** .  
  
2.  Щелкните заголовок нового столбца и введите **M/F**.  
  
### <a name="to-add-a-rectangle"></a>Добавление прямоугольника  
  
1.   На вкладке **Вставка** щелкните **Прямоугольник** , а затем щелкните ячейку данных в столбце **M/F** .  
  
     В ячейку будет добавлен прямоугольник.  
     
     ![руководство-по-выражениям-построителя-отчетов-вставка-прямоугольника](../reporting-services/media/report-builder-expression-tutorial-insert-rectangle.png)
  
2. Перетащите разделитель столбцов между столбцами **M/F/** и **Name** , чтобы сузить столбец **M/F** .

    ![руководство-по-выражениям-построителя-отчетов-сужение-столбца](../reporting-services/media/report-builder-expression-tutorial-narrow-column.png)
  
### <a name="to-use-color-to-show-gender"></a>Обозначение пола цветом  
  
1.  Щелкните правой кнопкой мыши прямоугольник в ячейке данных столбца **M/F** и выберите пункт **Свойства прямоугольника**.  
  
2.  В диалоговом окне **Свойства прямоугольника** на вкладке **Заливка** нажмите кнопку выражения **fx** рядом с текстовым полем **Цвет заливки**.  
  
3.  В диалоговом окне **Выражение** разверните узел **Общие функции** и выберите **Выполнение программы**.  
  
4.  В списке **Элемент** дважды щелкните **Switch**.  
  
5.  В списке **Категория** щелкните **Поля (выражения)**.  
  
6.  В списке **Значения** дважды щелкните **Gender**.  
  
7.  Введите **="Male",** (включая запятую).

8. В списке **Категория** выберите **Константы**, а в поле **Значения** щелкните **Васильковый**.

    ![руководство-по-выражениям-построителя-отчетов-цвет-васильковый](../reporting-services/media/report-builder-expression-tutorial-color-expression-cornflower-blue.png)

9. В конце введите запятую. 
  
5.  В списке **Категория** выберите **Поля (выражения)**, а в списке **Значения** дважды щелкните **Gender** (Пол) еще раз.  
  
7.  Введите **="Female",** (включая запятую). 

8. В списке **Категория** выберите **Константы**, а в поле **Значения** щелкните **Томатный**.

13. После этого введите закрывающую скобку **)** . 
  
    Законченное выражение выглядит следующим образом: `=Switch(Fields!Gender.Value ="Male", "CornflowerBlue",Fields!Gender.Value ="Female","Tomato")`  
    
    ![руководство-по-выражениям-построителя-отчетов-цвет-законченное-выражение](../reporting-services/media/report-builder-expression-tutorial-color-expression-complete.png)
  
12. Нажмите кнопку **ОК**, затем нажмите кнопку **ОК** еще раз, чтобы закрыть диалоговое окно **Свойства прямоугольника** .  
  
14. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  

    ![руководство-по-выражениям-построителя-отчетов-предпросмотр-столбец-m-f](../reporting-services/media/report-builder-expression-tutorial-preview-m-f-column.png)

### <a name="to-format-the-color-rectangles"></a>Форматирование цветных прямоугольников

1. Щелкните **Конструктор** для возврата в режим конструктора.  

16. Выберите прямоугольник в столбце **M/F** . На панели свойств в разделе "Граница" задайте следующие свойства.

    - BorderColor — White (Белый).
    - BorderStyle — Solid (Сплошной).
    - BorderWidth — 5pt.
    
    ![руководство-по-выражениям-построителя-отчетов-форматирование-столбца-m-f](../reporting-services/media/report-builder-expression-tutorial-format-m-f-column.png)

18. Нажмите кнопку **Выполнить** для предварительного просмотра отчета еще раз. На этот раз цветные блоки имеют границы белого цвета со всех сторон.

    ![руководство-по-выражениям-построителя-отчетов-предпросмотр-форматированного-столбца-m-f](../reporting-services/media/report-builder-expression-tutorial-preview-formatted-m-f-column.png)  
  
## <a name="Lookup"></a>5. Поиск значения в столбце CountryRegion  
В этом разделе вы создадите набор данных CountryRegion и при помощи функции **Lookup** отобразите название страны или региона вместо идентификатора.  
  
### <a name="to-create-the-countryregion-dataset"></a>Создание набора данных CountryRegion  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  В области данных отчета нажмите кнопку **Создать** и выберите **Набор данных**.  
  
3.  В окне "Свойства данных" ** выберите команду **Использовать набор данных, внедренный в отчет**.  
  
4.  В списке **Источник данных** выберите ExpressionsDataSource.  
  
5.  В поле **Имя** введите **CountryRegion**.  
  
6.  Убедитесь в том, что выбран тип запроса **Текст** , и нажмите кнопку **Конструктор запросов**.  
  
7.  Нажмите кнопку **Изменить как текст**.  
  
8.  Скопируйте и вставьте на панели запросов следующий запрос:  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. Чтобы запустить запрос, нажмите кнопку **Выполнить** (**!**).  
  
    Результатом запроса будут идентификаторы и названия стран и регионов.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Снова нажмите кнопку **ОК** , чтобы выйти из диалогового окна **Свойства набора данных** .  

     Теперь в столбце **Данные отчета** есть второй набор данных.
  
### <a name="to-look-up-values-in-the-countryregion-dataset"></a>Поиск значений в наборе данных CountryRegion  
  
1.  Щелкните заголовок столбца **Country Region ID** (ИД региона страны) и удалите **ID**, чтобы осталось только **Country Region**(Регион страны).  
  
2.  Щелкните правой кнопкой мыши ячейку для столбца **Country Region** и выберите пункт **Выражение**.  
  
3.  Удалите выражение, оставив знак равенства «=».  
  
    Оставшееся выражение: `=`  
  
4.  В диалоговом окне **Выражение** разверните узел **Общие функции** и выберите **Прочее**. В списке **Элемент** дважды щелкните **Lookup**.  
  
6.  В списке **Категория** выберите **Поля (выражения)**, а в списке **Значения** дважды щелкните **CountryRegionID**.  
  
8.  Поместите курсор сразу после `CountryRegionID.Value`и введите **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**.  
  
    Готовое выражение: `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`  
  
    Синтаксис функции **Lookup** задает поиск соответствия между CountryRegionID в наборе данных Expressions и ID в наборе данных CountryRegion, возвращающий значение CountryRegion из набора данных CountryRegion.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
## <a name="Count"></a>6. Подсчет дней с последней покупки  
В этом разделе вы добавите столбец и при помощи функции **Now** или встроенной глобальной переменной `ExecutionTime` рассчитаете число дней, прошедших с последней покупки клиента до текущей даты.  
  
### <a name="to-add-the-days-ago-column"></a>Добавление столбца Days Ago  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните правой кнопкой мыши столбец **Last Purchase** , наведите указатель на пункт **Вставить столбец**, а затем выберите пункт **Справа**.  
  
    Новый столбец будет добавлен справа от столбца **Last Purchase** .  
  
3.  В заголовке столбца введите **Days Ago**.  
  
4.  Щелкните правой кнопкой мыши ячейку столбца **Days Ago** и выберите пункт **Выражение**.  
  
5.  В диалоговом окне **Выражение** разверните узел **Общие функции** и выберите пункт **Дата и время**.  
  
6.  В списке **Элемент** дважды щелкните **DateDiff**.  
  
7.  Сразу после `DateDiff(`введите **"d",** (включая кавычки "" и запятую). 
  
9. В списке **Категория** выберите **Поля (выражения)**, а в списке **Значения** дважды щелкните **LastPurchase**.  
  
11. Сразу после `Fields!LastPurchase.Value`введите **,** (запятую). 
  
13. В списке **Категория** еще раз щелкните пункт **Дата и время**, а затем в списке **Элемент** дважды щелкните **Сейчас**.  
  
    > [!WARNING]  
    > В рабочих отчетах функцию **Now** нельзя использовать в выражениях, которые вычисляются многократно при подготовке отчета (например, в строках детализации отчета). Значение **Now** будет разным в разных строках, и эти различия повлияют на результаты вычислений, что может привести к некоторой несогласованности результатов. Вместо этого необходимо пользоваться глобальной переменной `ExecutionTime` , имеющейся в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
15. Удалите левую скобку после `Now(`, а затем введите правую скобку **)**.  
  
    Законченное выражение выглядит следующим образом: `=DateDiff("d", Fields!LastPurchase.Value, Now)`  
    
    ![руководство-по-выражениям-построителя-отчетов-дней-с-последней-покупки](../reporting-services/media/report-builder-expression-tutorial-date-since-last-purchase.png)
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  

11. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
## <a name="Indicator"></a>7. Отображение сравнения цен с помощью индикатора  
В этом разделе вы добавите новый столбец и индикатором покажете, превышают ли покупки определенного человека за последний год (YTD) среднее значение YTD. Функция **Round** округляет значения до целого числа.  
  
Настройка индикатора и его состояний осуществляется в несколько шагов. При необходимости инструкции в разделе "Настройка индикатора" можно пропустить, скопировав и вставив готовые выражения из этого руководства в диалоговое окно **Выражение** .  
  
### <a name="to-add-the--or---avg-sales-column"></a>Добавление столбца «+ or - AVG Sales»  
  
1.  Щелкните правой кнопкой мыши столбец **YTD Purchase** , наведите указатель на пункт **Вставить столбец**, а затем выберите пункт **Справа**.  
  
    Новый столбец будет добавлен справа от столбца **YTD Purchase** .  
  
2.  Щелкните заголовок столбца и введите **+ or – AVG Sales**.  
  
### <a name="to-add-an-indicator"></a>Добавление индикатора  
  
1.  На вкладке **Вставка** щелкните **Индикатор**, а затем — ячейку данных для столбца **+ or – AVG Sales** .  
  
    Откроется диалоговое окно **Выбор стиля индикатора** .  
  
2.  В группе наборов значков **Направляющие** щелкните набор из трех серых стрелок.  

    ![руководство-по-выражениям-построителя-отчетов-выбор-индикатора](../reporting-services/media/report-builder-expression-tutorial-select-indicator.png)
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-configure-the-indicator"></a>Настройка индикатора  
  
1.  Щелкните индикатор правой кнопкой мыши, выберите пункт **Свойства индикатора**, а затем щелкните **Значение и состояния**.  
  
2.  Нажмите кнопку выражения **fx** рядом с текстовым полем **Значение** .  
  
3.  В диалоговом окне **Выражение** разверните узел **Общие функции**и выберите **Математические**.  
  
4.  В списке **Элемент** дважды щелкните **Round**.  
  
5.  В списке **Категория** выберите **Поля (выражения)**, а в списке **Значения** дважды щелкните **YTDPurchase**.  
  
7.  Сразу же после `Fields!YTDPurchase.Value`введите  **-** (знак "минус"). 
  
9. Еще раз разверните **Общие функции** щелкните **Статистическое**, а затем в списке **Элемент** дважды щелкните **Avg**.  
  
11. В списке **Категория** выберите **Поля (выражения)**, а в списке **Значения** дважды щелкните **YTDPurchase**.  
  
13. Сразу же после `Fields!YTDPurchase.Value`введите **, "Expressions"))**.  
  
    Законченное выражение выглядит следующим образом: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. В поле **Единица измерения состояний** выберите **Число**.  
  
17. В строке со стрелкой вниз нажмите кнопку **fx** справа от текстового поля для значения **Начало** .  

    ![руководство-по-выражениям-построителя-отчетов-индикатор-начало](../reporting-services/media/report-builder-expression-tutorial-indicator-start.png)
  
18. В диалоговом окне **Выражение** разверните узел **Общие функции**и выберите **Математические**.  
  
19. В списке **Элемент** дважды щелкните **Round**.  
  
20. В списке **Категория** выберите **Поля (выражения)**, а в списке **Значения** дважды щелкните **YTDPurchase**.  
  
22. Сразу же после `Fields!YTDPurchase.Value`введите  **-** (знак "минус"). 
  
24. Еще раз разверните **Общие функции** , щелкните **Статистическое**, а затем в списке **Элемент** дважды щелкните **Avg**.  
  
26. В списке **Категория** выберите **Поля (выражения)**, а в списке **Значения** дважды щелкните **YTDPurchase**.  
  
28. Сразу же после `Fields!YTDPurchase.Value` введите **, "Expressions")) < 0**.  
  
    Готовое выражение: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. В текстовом поле для значения **Конец** введите **0**  
  
32. Щелкните строку, где находится горизонтальная стрелка, а затем щелкните **Удалить**.  

    ![руководство-по-выражениям-построителя-отчетов-состояние-индикатора](../reporting-services/media/report-builder-expression-tutorial-delete-indicator-state.png)
    
    Сейчас есть только две стрелки — вверх или вниз.
  
33. В строке со стрелкой вверх в поле **Начало** введите **0**  
  
34. Нажмите кнопку **fx** справа от текстового поля для значения **Конец** .  
  
35. В диалоговом окне **Выражение** удалите **100** и введите выражение: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. Снова нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Свойства индикатора** .  
  
38. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  

    ![руководство-по-выражениям-построителя-отчетов-предпросмотр-индикатора](../reporting-services/media/report-builder-expression-tutorial-preview-indicator.png)
  
## <a name="GreenBar"></a>8. Создание отчета с чередованием строк  
Создайте параметр, чтобы пользователи отчета могли задавать цвет, который будет применяться для чередования строк в отчете.  
  
### <a name="to-add-a-parameter"></a>Добавление параметра  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  На панели **Данные отчета** щелкните правой кнопкой мыши узел **Параметры** и выберите команду **Добавить параметр**.  

    ![руководство-по-выражениям-построителя-отчетов-добавление-параметра](../reporting-services/media/report-builder-expression-tutorial-add-parameter.png)
  
    Откроется диалоговое окно **Свойства параметра отчета** .  
  
3.  В поле **Подсказка**введите **Выберите цвет**  
  
4.  В поле **Имя**введите **RowColor**  
  
5.  На вкладке **Доступные значения** выберите **Указать значения**.  
  
7.  Нажмите кнопку **Добавить**.  
  
8.  В поле **Метка** введите **Yellow**  
  
9. В поле **Значение** введите **Yellow**  
  
10. Нажмите кнопку **Добавить**.  
  
11. В поле **Метка** введите **Green**  
  
12. В поле **Значение** введите **PaleGreen**  
  
13. Нажмите кнопку **Добавить**.  
  
14. В поле **Метка** введите **Blue**  
  
15. В поле **Значение** введите **LightBlue**  
  
16. Нажмите кнопку **Добавить**.  
  
17. В поле **Метка** введите **Pink**  
  
18. В поле **Значение** введите **Pink**  

    ![руководство-по-выражениям-построителя-отчетов-доступный-параметр](../reporting-services/media/report-builder-expression-tutorial-parameter-available.png)
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-apply-alternating-colors-to-detail-rows"></a>Применение цветов чередования строк детализации  
  
1.   Выберите все ячейки в строке данных, за исключением ячейки в столбце **M/F** , который имеет собственный цвет фона.  

     ![руководство-по-выражениям-построителя-отчетов-выбор-чередование](../reporting-services/media/report-builder-expression-tutorial-select-banded.png)
  
4.  На панели свойств щелкните **BackgroundColor**. 

     Если панель свойств не отображается, перейдите на вкладку **Вид** и установите флажок **Свойства** .  
  
    Если в области свойств последние указаны по категориям, **BackgroundColor** можно найти в категории **Прочее** .  
  
5.  Нажмите стрелку вниз и выберите **Выражение**.  

    ![руководство-по-выражениям-построителя-отчетов-свойство-чередования-цвета](../reporting-services/media/report-builder-expression-tutorial-banded-color-property.png)
  
6.  В диалоговом окне **Выражение** разверните узел **Общие функции**и выберите **Выполнение программы**.  
  
7.  В списке **Элемент** дважды щелкните **IIf**.  
  
8.  В списке **Общие функции**щелкните **Прочее**и в списке **Элемент** дважды щелкните **RowNumber**.  

9. Сразу же после **RowNumber(** введите **Nothing) MOD 2,**.
  
8. Щелкните **Параметры** и в списке **Значения** дважды щелкните **RowColor**.  
  
22. Сразу же после `Parameters!RowColor.Value`введите **, "White")**  
  
    Законченное выражение выглядит следующим образом: `=IIF(RowNumber(Nothing) MOD 2, Parameters!RowColor.Value, “White”)`  
    
    ![руководство-по-выражениям-построителя-отчетов-чередование-цветов](../reporting-services/media/report-builder-expression-tutorial-banded-color-expressn.png)
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="run-the-report"></a>Запустите отчет.  
  
1.  На вкладке **Главная** нажмите кнопку **Выполнить**.  

    Теперь при запуске отчет будет отображаться только после выбора цвета для небелых полос.
  
3.  В списке **Выберите цвет** выберите цвет для небелых полос в отчете.  
    
    ![руководство-по-выражениям-построителя-отчетов-выбор-цвета](../reporting-services/media/report-builder-expression-tutorial-select-color.png)
  
4.  Нажмите кнопку **Просмотр отчета**.  
  
    Отчет будет подготовлен к просмотру с выбранным цветом фона чередующихся строк. 
    
    ![руководство-по-выражениям-построителя-отчетов-предпросмотр-чередование](../reporting-services/media/report-builder-expression-tutorial-preview-banded.png) 
  
## <a name="Title"></a>(Необязательно) Добавление заголовка отчета  
Добавим заголовок отчета.  
  
### <a name="to-add-a-report-title"></a>Добавление заголовка отчета  
  
1.  В области конструктора щелкните ссылку **Щелкните, чтобы добавить заголовок**.  
  
2.  Введите **Sales Comparison Summary**(Сравнительная сводка по продажам), а затем выделите текст.  
  
3.  На вкладке **Главная** в окне **Шрифт** установите следующие значения:

    -  Размер — 18.
    -  Цвет — серый.
    -  Полужирный
  
4.  На вкладке **Главная** нажмите кнопку **Выполнить**.  
  
3.  Выберите цвет для небелых полос в отчете и щелкните **Просмотреть отчет**.  
  
## <a name="Save"></a>(Необязательно) Сохранение отчета  
Отчеты можно сохранять на сервере отчетов, в библиотеке SharePoint или на компьютере. Дополнительные сведения см. в разделе [Сохранение отчетов (построитель отчетов)](../reporting-services/report-builder/saving-reports-report-builder.md).  
  
В этом руководстве вы сохраните отчет на сервере отчетов. Если нет доступа к серверу отчетов, сохраните отчет на компьютере.  
  
### <a name="to-save-the-report-to-a-report-server"></a>Сохранение отчета на сервере отчетов  
  
1.  В меню **Файл** выберите команду **Сохранить как**.  
  
2.  Нажмите кнопку **Последние сайты и серверы**.  
  
3.  Выберите или введите имя сервера отчетов, для которого существует разрешение на сохранение отчетов.  
  
    Появится сообщение «Соединение с сервером отчетов». После того как соединение установлено, пользователю представляется содержимое папки, заданной администратором сервера отчетов в качестве места хранения отчетов по умолчанию.  
  
4.  Введите имя отчета и нажмите кнопку **Сохранить**.  
  
Отчет будет сохранен на сервере отчетов. Имя сервера отчетов, с которым установлено соединение, будет отображено в строке состояния в нижней части окна.

Теперь пользователи смогут найти ваш отчет на веб-портале [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] .

![руководство-по-выражениям-построителя-отчетов-окончание-в-браузере](../reporting-services/media/report-builder-expression-tutorial-final-in-browser.png)

   
## <a name="see-also"></a>См. также:  
[Выражения (построитель отчетов и службы SSRS)](../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
[Примеры выражений (построитель отчетов и службы SSRS)](../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
[Индикаторы (построитель отчетов и службы SSRS)](../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
[Изображения, текстовые поля, прямоугольники и линии (построитель отчетов и службы SSRS)](../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md)  
[Таблицы (построитель отчетов и службы SSRS)](../reporting-services/report-design/tables-report-builder-and-ssrs.md)  
[Наборы данных отчетов (службы SSRS)](../reporting-services/report-data/report-datasets-ssrs.md)  
  
  
  


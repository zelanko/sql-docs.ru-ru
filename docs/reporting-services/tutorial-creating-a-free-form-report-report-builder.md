---
title: Учебник. Создание отчета в свободной форме (построитель отчетов) | Документы Майкрософт
description: Узнайте, как создать отчет с разбивкой на страницы, который выступает в качестве информационного бюллетеня и на каждой странице которого выводится статический текст, сводные визуальные элементы и образец подробных данных по продажам.
ms.date: 09/02/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6b189c494f887faca2b6d3d4bb00253992470132
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247463"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a>Руководство по Создание отчета в свободной форме (построитель отчетов)
В этом учебнике вы создадите отчет с разбивкой на страницы в качестве информационного бюллетеня. На каждой странице выводится статический текст, сводные визуальные элементы и образец подробных данных по продажам.

![report-builder-free-form-report-complete](../reporting-services/media/report-builder-free-form-report-complete.png)

Отчет группирует сведения по территории и отображает имя менеджера по продажам на данной территории, а также подробные и сводные сведения о продажах. Вы начнете с создания области списка данных, которая используется как основа отчета в свободной форме, затем добавите декоративную панель с изображением, статический текст со вставленными данными, таблицу для отображения подробной информации и при необходимости круговые диаграммы и гистограммы со сводными данными.  
  
На изучение этого руководства потребуется примерно 20 минут.  
  
## <a name="requirements"></a>Требования  
Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/prerequisites-for-tutorials-report-builder.md).  
  
## <a name="1-create-a-blank-report-data-source-and-dataset"></a><a name="BlankReport"></a>1. Создание пустого отчета, источника данных и набора данных  
  
> [!NOTE]  
> В этом учебнике запрос уже содержит значения данных, поэтому внешний источник данных не требуется. В связи с этим запрос получается весьма длинным. В рабочей среде запрос не будет содержать данные. Этот запрос содержит данные только в учебных целях.  
  
### <a name="to-create-a-blank-report"></a>Создание пустого отчета  
  
1.  [Запустите построитель отчетов](../reporting-services/report-builder/start-report-builder.md) с компьютера, веб-портала [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] или сервера в режиме интеграции с SharePoint.  
  
    Откроется диалоговое окно **Создать отчет или набор данных** .  
  
    Если диалоговое окно **Новый отчет или набор данных** не появилось, в меню **Файл** выберите команду **Создать**.  
  
2.  Убедитесь в том, что на левой панели выбран **Новый отчет** . 
 
3.  На правой панели щелкните **Пустой отчет**.  
  
### <a name="to-create-a-new-data-source"></a>Создание нового источника данных  
  
1.  В области данных отчета нажмите кнопку **Создать** > **Источник данных**.  
  
2.  В поле **Имя** введите **ListDataSource**  
  
3.  Нажмите кнопку **Использовать соединение, внедренное в отчет**.  
  
4.  Убедитесь в том, что выбран тип соединения Microsoft SQL Server, а затем в поле **Строка подключения** введите: **Источник данных = \<servername>**  
  
    Значение **\<servername>** , например Report001, указывает компьютер, на котором установлен экземпляр яда СУБД SQL Server. Так как данные для этого отчета не извлекаются из базы данных SQL Server, не нужно указывать имя базы данных. База данных по умолчанию на указанном сервере используется только для синтаксического анализа запроса.  
  
5.  Нажмите **Учетные данные**и введите учетные данные, необходимые для подключения к экземпляру ядра СУБД SQL Server.  
  
6.  Нажмите кнопку **ОК**.  
  
### <a name="to-create-a-new-dataset"></a>Создание нового набора данных  
  
1.  В области данных отчета щелкните **Создать** > **Набор данных**.  
  
2.  В поле **Имя** введите **ListDataset**.  
  
3.  Нажмите **Использовать включенный в мой отчет набор данных**, проверьте, что в качестве источника данных указан **ListDataSource**.  
  
4.  Убедитесь, что выбран тип запроса **Текст** , и нажмите кнопку **Конструктор запросов**.  
  
5.  Нажмите кнопку **Изменить как текст**.  
  
6.  Скопируйте и вставьте на панели запросов следующий запрос:  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
7.  Щелкните значок **Запуск** (!), чтобы запустить запрос.  
  
    Результаты запроса — это данные, доступные для отображения в отчете.  
  
    ![report-builder-free-form-tutorial-data](../reporting-services/media/report-builder-free-form-tutorial-data.png) 
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="2-add-and-configure-a-list"></a><a name="List"></a>2. Добавление и настройка списка  
В [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] область списка данных идеально подходит для создания отчетов произвольной формы. Она основана на области данных *tablix* , так же как таблицы и матрицы. Дополнительные сведения см. в разделе [Создание счета-фактуры и формы со списками](../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
Список будет использоваться для отображения сведений о территориальных продажах в отчете, отформатированном как информационный бюллетень. Сведения группируются по территориям. Добавьте новую группу строк, в которой данные группируются по территориям, а затем удалите встроенную группу строк подробностей.  
  
### <a name="to-add-a-list"></a>Добавление списка  
  
1.  На вкладке **Вставка** щелкните **Области данных** > **Список**. 

2. Щелкните в области текста отчета (между заголовком и областью нижнего колонтитула) и перетащите указатель, чтобы создать поле со списком. Установите для списка высоту в 7 дюймов и ширину в 6,25 дюйма. Чтобы задать точный размер, в области **Свойства** в разделе **Положение**введите значения свойств **Ширина** и **Высота** .
  
    > [!NOTE]  
    > Для отчета используются размер бумаги Letter (8,5 X11) и поля шириной 1 дюйм. Поле со списком высотой более 9 дюймов или шириной более 6,5 дюймов может привести к формированию пустых страниц.  
  
2.  Щелкните внутри поля со списком, щелкните правой кнопкой мыши панель вверху списка и выберите пункт **Свойства табликса**.  
  
    ![report-builder-free-form-tablix-properties](../reporting-services/media/report-builder-free-form-tablix-properties.png) 
  
3.  В раскрывающемся списке **Имя набора данных** выберите пункт **ListDataset**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Щелкните правой кнопкой мыши внутри списка и выберите пункт **Свойства прямоугольной области**.  
  
6.  На вкладке **Общие** установите флажок **Вставить разрыв страницы после** .  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a>Добавление новой группы строк и удаление группы подробностей  
  
1.  На панели "Группы строк" щелкните правой кнопкой мыши группу подробностей, выберите пункт **Добавить группу**, а затем пункт **Родительская группа**.  
  
    ![report-builder-free-form-add-parent-group](../reporting-services/media/report-builder-free-form-add-parent-group.png)  
  
2.  В списке **Группировать по** выберите `[Territory].`  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    Столбец, содержащий ячейку `[Territory]` , будет добавлен в список.
  
4.  Щелкните правой кнопкой мыши столбец "Территория" в списке и выберите команду **Удалить столбцы**.  
  
    ![report-builder-free-form-delete-columns](../reporting-services/media/report-builder-free-form-delete-columns.png)
  
5.  Выберите **Удалить только столбцы**.  
  
6.  На панели "Группы строк" щелкните правой кнопкой мыши группу **Подробности** и выберите пункт **Удалить группу**.  
   
7.  Выберите **Удалить только группу**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="3-add-graphic-elements"></a><a name="Graphics"></a>3. Добавление графических элементов  
Одно из преимуществ области списка данных заключается в возможности добавлять в любом месте такие элементы отчета, как прямоугольники и текстовые поля, не ограничиваясь табличным макетом. Внешний вид отчета улучшается благодаря добавлению графических элементов (прямоугольника с цветной заливкой).  
  
### <a name="to-add-graphic-elements-to-the-report"></a>Добавление графических элементов в отчет  
  
1.  На вкладке **Вставка** выберите **Прямоугольник**. 

2. Щелкните в левом верхнем углу списка и перетащите указатель, чтобы создать прямоугольник с длиной в 17,78 см и шириной 8,89 см. Чтобы задать точный размер, в области **Свойства** в разделе **Положение**введите значения свойств **Ширина** и **Высота**.
  
2.  Щелкните правой кнопкой мыши прямоугольник и выберите пункт **Свойства прямоугольника**.  
  
3.  Перейдите на вкладку **Заливка** .  
  
4.  В поле **Цвет заливки**выберите значение **Светло-серый**.  
   
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
В левой стороне отчета теперь находится вертикальный графический элемент, состоящий из светло-серого прямоугольника, как показано на рисунке ниже.  
  
![report-builder-free-form-gray-rectangle](../reporting-services/media/report-builder-free-form-gray-rectangle.png)
 
## <a name="4-add-free-form-text"></a><a name="Text"></a>4. Добавление произвольного текста  
Вы можете добавлять текстовые поля, которые содержат статический текст, повторяемый на каждой странице отчета, а также поля данных.  
  
### <a name="to-add-text-to-the-report"></a>Добавление текста в отчет  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  На вкладке **Вставка** щелкните **Текстовое поле**. Щелкните в левом верхнем углу списка внутри ранее добавленного прямоугольника и перетащите указатель, чтобы создать текстовое поле шириной приблизительно 3,45 дюйма и высотой приблизительно 5 дюймов.  
  
3.  Поместите курсор в текстовое поле и введите **Информационный бюллетень для**. После слова "для" поставьте пробел, отделяющий этот текст от поля, которое вы добавите в следующем шаге.   
  
    ![Добавление текста заголовка бюллетеня](../reporting-services/media/tutorial-newsletterfor.png "Добавление текста заголовка бюллетеня")  
  
4.  Перетащите поле `[Territory]` из ListDataSet в области "Данные отчета" в текстовое поле и поместите его после надписи "Информационный бюллетень для ".  
  
    ![report-builder-free-form-territory-field](../reporting-services/media/report-builder-free-form-territory-field.png)
  
5.  Выделите текст и поле `[Territory]` .  
  
6.  На вкладке **Главная** в разделе **Шрифт** выберите следующие значения: 
  
    *  **Segoe Semibold**.
    *  **20 пт**.
    *  **Томатный**.  
  
9. Поместите курсор ниже текста, введенного в шаге 3, и введите **Здравствуйте,** , поставив после запятой пробел, отделяющий этот текст от поля, которое вы добавите в следующем шаге.  
 
10. Перетащите поле `[FullName]` из ListDataSet в области "Данные отчета" в текстовое поле и поместите его после надписи "Здравствуйте, ", а затем введите восклицательный знак (!).  
   
11. Выделите текст, добавленный в предыдущем шаге.
  
12. На вкладке **Главная** в разделе **Шрифт** выберите следующие значения: 
  
    *  **Segoe Semibold**.
    *  **16 пт**.
    *  **Черный**.  
   
15. Разместите курсор ниже текста, добавленного в шагах с 9 по 13, а затем скопируйте и вставьте следующий текст-заполнитель:  
  
    ```  
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. 
    Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. 
    Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque.   
 
    ```  
  
16. Выделите добавленный текст.  
  
17.  На вкладке **Главная** в разделе **Шрифт** выберите следующие значения: 
  
      *  **Segoe UI**.
      *  **10 пт**.
      *  **Черный**.  
 
20. Поместите курсор в текстовом поле ниже текста-заполнителя и введите **Поздравляем с общим объемом продаж**, поставив в конце пробел, отделяющий этот текст от поля, которое вы добавите в следующем шаге. 
  
21. Перетащите поле Sales в текстовое поле, поместите его после текста, введенного в предыдущем шаге, а затем поставьте восклицательный знак (!).  

25. Выделите текст и только что добавленное поле.  
  
17.  На вкладке **Главная** в разделе **Шрифт** выберите следующие значения: 
  
      *  **Segoe Semibold**.
      *  **16 пт**.
      *  **Черный**.  
  
22. Выделите только поле `[Sales]`, щелкните его правой кнопкой мыши и выберите пункт **Выражение**.  
  
23. В поле **Выражение** измените выражение, включив функцию Sum следующим образом:  
  
    ```  
    =Sum(Fields!Sales.value)  
    ```  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    ![report-builder-free-form-text-box](../reporting-services/media/report-builder-free-form-text-box.png)
 
29. Не снимая выделение с поля `[Sum(Sales)]`, на вкладке **Главная** в группе **Число** нажмите кнопку **Денежный**.  
  
30. Щелкните правой кнопкой текстовое поле с текстом "Щелкните, чтобы добавить заголовок", а затем нажмите кнопку **Удалить**.  
  
31. Выберите поле со списком. Выделите две двусторонние стрелки и переместите их в верхнюю часть страницы.  

    ![report-builder-drag-list](../reporting-services/media/report-builder-drag-list.png)
  
32. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
В отчете отображается статический текст, и каждая страница отчета содержит данные для определенной территории. Данные о продажах форматируются как денежные значения.  
  
![report-builder-newsletter-page-preview](../reporting-services/media/report-builder-newsletter-page-preview.png)
  
## <a name="5-add-a-table-to-show-sales-details"></a><a name="Table"></a>5. Добавление таблицы для показа подробностей о продажах  
Используйте мастер создания новой таблицы или матрицы, чтобы добавить таблицу в отчет произвольной формы. После завершения работы мастера добавьте вручную строку для итогов.  
  
### <a name="to-add-a-table"></a>Добавление таблицы  
  
1.  На вкладке **Вставка** в области **Области данных** щелкните **Таблица** > **Мастер таблиц**.  
  
2.  На странице **Выбор набора данных** выберите **ListDataset** > **Далее**.  
  
4.  На странице **Выравнивание полей** перетащите поле Product из раздела **Доступные поля** в **Значения**.  
  
5.  Повторите шаг 3 для полей SalesDate, Quantity и Sales. Поместите SalesDate ниже Product, Quantity ниже SalesDate, а Sales ниже SalesDate.  
  
6.  Щелкните **Далее**.  
  
7.  На странице **Выбор макета** можно просмотреть макет таблицы.  
  
    Таблица очень проста: пять столбцов без строк или групп столбцов. Поскольку группы отсутствуют, недоступны варианты макета, связанные с группами. Далее в учебнике таблица будет обновлена вручную для добавления итога.  
  
8.  Щелкните **Далее**.  
  
9. Нажмите кнопку **Готово**.  
  
11. Перетащите таблицу ниже текстового поля, добавленного в занятии 4.  
  
    > [!NOTE]  
    > Убедитесь в том, что таблица находится внутри поля со списком и серого прямоугольника.  
  
12. Выбрав таблицу, в области **Группа строк** щелкните правой кнопкой мыши элемент **Сведения** > **Добавить итог** > **После**.  
  
    ![report-builder-free-form-table-totals](../reporting-services/media/report-builder-free-form-table-totals.png)
  
13. Выделите ячейку в столбце Product и введите **Итого**.

    ![report-builder-free-form-type-total](../reporting-services/media/report-builder-free-form-type-total.png)

12. Выберите поле [SalesDate]. На вкладке **Главная** в разделе **Число** измените значение **По умолчанию** на **Дата**.

13. Выберите поля [Sum(Sales)]. На вкладке **Главная** в разделе **Число** измените значение **По умолчанию** на **Денежный**.

Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
Отчет отображает таблицу со сведениями о продажах и итогами.  
  
![report-builder-free-form-with-table](../reporting-services/media/report-builder-free-form-with-table.png)
   
## <a name="6-save-the-report"></a><a name="Save"></a>6. Сохранение отчета  
Отчеты можно сохранять на сервере отчетов, в библиотеке SharePoint или на компьютере.  
  
В данном учебнике предусмотрено сохранение отчета на сервере отчетов. Если нет доступа к серверу отчетов, сохраните отчет на компьютере.  
  
### <a name="to-save-the-report-on-a-report-server"></a>Сохранение отчета на сервере отчетов  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Нажмите кнопку **Последние сайты и серверы**.  
  
3.  Выберите или введите имя сервера отчетов, для которого существует разрешение на сохранение отчетов.  
  
    Появится сообщение «Соединение с сервером отчетов». После того как соединение установлено, пользователю представляется содержимое папки, заданной администратором сервера отчетов как место по умолчанию для отчетов.  
  
4.  В поле **Имя**замените имя по умолчанию на **SalesInformationByTerritory**.  
  
5.  Выберите команду **Сохранить**.  
  
Отчет будет сохранен на сервере отчетов. Имя сервера отчетов, с которым установлено соединение, будет отображено в строке состояния в нижней части окна.  
  
### <a name="to-save-the-report-on-your-computer"></a>Сохранение отчета на компьютере  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Перейдите на **Рабочий стол**, откройте папку **Мои документы**или **Мой компьютер**и перейдите в папку, в которую нужно сохранить отчет.  
  
3.  В поле **Имя**замените имя по умолчанию на **SalesInformationByTerritory**.  
  
4.  Выберите команду **Сохранить**.  
  
## <a name="7-optional-add-a-line-to-separate-areas-of-the-report"></a><a name="Line"></a>7. Добавление строки в отдельные области отчета (необязательно)  
Добавление строки в отдельные области редактирования и подробностей отчета.  
  
### <a name="to-add-a-line"></a>Добавление линии  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  На вкладке **Вставка** выберите **Элементы отчета** > **Линия**.  
  
3.  Проведите линию ниже текстового поля, добавленного на занятии 4.  
  
4.  Щелкните линию, а затем на вкладке **Главная** в разделе **Граница** выберите следующие значения:
     * Для параметра**Ширина** выберите значение **3 пт** .
     * Для параметра**Цвет** выберите значение **Томатный**.  
  
## <a name="8-optional-add-summary-data-visualizations"></a><a name="Visualization"></a>8. Добавление представлений сводных данных (необязательно)  
С помощью прямоугольников можно управлять подготовкой отчетов к просмотру. Поместите круговую диаграмму и гистограмму в прямоугольник, чтобы отчет был правильно подготовлен к просмотру.  
  
### <a name="to-add-a-rectangle"></a>Добавление прямоугольника  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  На вкладке **Вставка** выберите **Элементы отчета** >  **Прямоугольник**. Путем перетаскивания создайте в поле со списком справа от таблицы прямоугольник шириной приблизительно 2,25 дюйма и высотой приблизительно 7,9 дюйма.  
  
3.  Выделите новый прямоугольник, а затем в области "Свойства" установите значения **BorderColor — LightGrey**, **BorderStyle — Solid**и **BorderWidth — 2 pt**. 

4. Выровняйте верхний край прямоугольника с верхним краем таблицы.  
  
## <a name="to-add-a-pie-chart"></a>Добавление круговой диаграммы  
  
1.  На вкладке **Вставка** выберите **Визуализации данных** > **Диаграмма** > **Мастер диаграмм**.  
  
2.  На странице **Выбор набора данных** выберите **ListDataset** > **Далее**.  
  
3.  Щелкните **Круговая** > **Далее**.  
  
4.  На странице "Размещение полей диаграммы" перетащите поле Product в **Категории**.  
  
5.  Перетащите поле Quantity в **Значения**, а затем нажмите кнопку **Далее**.  
  
6.  Нажмите кнопку **Готово**.  
  
8.  Измените размеры диаграммы, показанной в левом верхнем углу отчета, установив ширину 2,25 дюйма и высоту 3,6 дюйма.  
  
9. Перетащите диаграмму в прямоугольник.  
   
10. Выделите заголовок диаграммы и введите **Проданные объемы товаров**.  
  
12. На вкладке **Главная** в разделе **Шрифт** установите следующие значения для заголовка:
    * **Шрифт** **Segoe UI Semibold**.
    * **Размер** **12 пт**.
    * **Цвет** **черный**.  

13. Щелкните правой кнопкой мыши условные обозначения и выберите пункт **Свойства условных обозначений**.

14. На вкладке **Общие** в разделе **Местоположение условных обозначений**выберите центральную точку внизу. 
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  

16. При необходимости сделайте область диаграммы выше путем перетаскивания.

     ![report-builder-free-form-pie](../reporting-services/media/report-builder-free-form-pie.png)
  
## <a name="to-add-a-column-chart"></a>Добавление гистограммы  
  
1.  На вкладке **Вставка** выберите **Визуализации данных** > **Диаграмма** > **Мастер диаграмм**.  
  
2.  На странице **Выбор набора данных** нажмите **ListDataset**, а затем нажмите кнопку **Далее**.  
  
3.  Выберите **Столбец**, а затем нажмите кнопку **Далее**.  
  
4.  На странице **Размещение полей диаграммы** перетащите поле Product на панель **Категории**.  
  
5.  Перетащите поле Sales в **Значения** , а затем нажмите кнопку **Далее**.  
  
    Значения отображаются по вертикальной оси.  
  
6.  Нажмите кнопку **Готово**.  
  
    Гистограмма добавляется в верхний левый угол отчета.  
  
8.  Измените размер диаграммы, установив ширину 2,25 дюйма и высоту почти 4 дюйма.  
  
9. Перетащите диаграмму внутрь прямоугольника ниже круговой диаграммы.  
   
10. Выделите заголовок диаграммы и введите **Продажи товаров**.  
  
12. На вкладке **Главная** в разделе **Шрифт** установите следующие значения для заголовка:
    * **Шрифт** **Segoe UI Semibold**.
    * **Размер** **12 пт**.
    * **Цвет** **черный**.  
  
15. Щелкните правой кнопкой мыши условные обозначения и выберите команду **Удалить условные обозначения**.  
  
    > [!NOTE]  
    > Если удалить условные обозначения, диаграмма небольшого размера станет удобнее для восприятия.  
  
    ![report-builder-free-form-column](../reporting-services/media/report-builder-free-form-column.png)

12. Выделите ось диаграммы, а затем на вкладке **Главная** выберите **Число** > **Денежный**.

13. Два раза нажмите кнопку **Уменьшить разрядность** , чтобы отображались только рубли, но не копейки.      
### <a name="to-verify-the-charts-are-inside-the-rectangle"></a>Проверка местонахождения диаграмм внутри прямоугольника  

Прямоугольники можно использовать как контейнеры для других элементов на странице отчета. Дополнительные сведения см. в [этом разделе](../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md).
  
1.  Выделите прямоугольник, который вы создали и в который добавили диаграммы ранее на этом занятии.  
  
    Свойство **Name** на панели «Свойства» показывает имя прямоугольника.  
  
    ![report-builder-free-form-rectangle-name](../reporting-services/media/report-builder-free-form-rectangle-name.png) 
  
2.  Щелкните круговую диаграмму.  
  
3.  Проверьте, что свойство **Parent** на панели **Свойства** показывает имя прямоугольника.  
  
     ![report-builder-free-form-pie-parent](../reporting-services/media/report-builder-free-form-pie-parent.png) 
  
4.  Щелкните гистограмму и повторите шаг 3.  
  
    > [!NOTE]  
    > Если диаграммы не находятся внутри прямоугольника, то не отображаются вместе в подготовленном к просмотру отчете.  
  
### <a name="to-make-the-charts-the-same-size"></a>Придание одинаковых размеров диаграммам  
  
1.  Выделите круговую диаграмму, нажмите клавишу CTRL, а затем выделите гистограмму.  
  
2.  Выделив обе диаграммы, щелкните их правой кнопкой мыши и выберите пункты **Макет** > **Установить ту же ширину**.  
  
    > [!NOTE]  
    > Элемент, который вы щелкнули сначала, задает ширину для всех выбранных элементов.  
  
3.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
Теперь отчет содержит сводные данные о продажах в круговых диаграммах и гистограммах.  
  

  
## <a name="next-steps"></a>Next Steps  
На этом работа с учебником по созданию отчета произвольной формы закончена.  
  
Дополнительные сведения о списках см. в следующих разделах: 
* [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md) 
* [Создание счета-фактуры и формы со списками](../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)
* [Ячейки, строки и столбцы области данных табликса (построитель отчетов и службы SSRS)](../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)  
  
См. подробнее о конструкторах запросов в руководствах по [средствам проектирования запросов (SSRS)](report-data/query-design-tools-ssrs.md) и [пользовательскому интерфейсу текстового конструктора запросов (построитель отчетов)](../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
## <a name="see-also"></a>См. также:  
[Учебники по построителю отчетов](../reporting-services/report-builder-tutorials.md) 
  


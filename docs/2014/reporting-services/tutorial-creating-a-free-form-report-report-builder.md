---
title: Учебник. Создание отчета в свободной форме (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 332c67f47c8096cbeb5a94c4e2a288cd532038cf
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66098950"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a>Учебник. Создание отчета в свободной форме (построитель отчетов)
  В этом учебнике объясняется, как создать отчет SQL Server Reporting Services произвольной формы в виде стандартного письма. Вы можете упорядочить элементы отчета, чтобы создать форму с текстовыми полями, изображениями и другими областями данных.  
  
 Отчет, который вы создаете в этом учебнике, строится на основе образца данных по продажам, включенного в учебник. Отчет группирует сведения по территории и отображает имя менеджера по продажам на данной территории, а также подробные и сводные сведения о продажах. Область списка данных используется как основа отчета в свободной форме, затем добавляются декоративная панель с изображением, статический текст со вставленными данными, таблица для отображения подробной информации и при необходимости круговые диаграммы и гистограммы со сводными данными.  
  
##  <a name="BackToTop"></a> Новые знания  
 В этом учебнике рассматриваются следующие темы:  
  
-   [Создание пустого отчета, источника данных и набора данных](#BlankReport)  
  
-   [Добавление и настройка списка](#List)  
  
-   [Добавление графических элементов](#Graphics)  
  
-   [Добавление произвольного текста](#Text)  
  
-   [Добавление таблицы для показа подробностей](#Table)  
  
-   [Форматирование данных](#Format)  
  
-   [Сохранение отчета](#Save)  
  
### <a name="other-optional-steps"></a>Другие дополнительные шаги  
  
-   [Добавление строки в отдельные области отчета](#Line)  
  
-   [Добавление отображения сводных данных](#Visualization)  
  
 Предполагаемое время для выполнения заданий данного учебника: 20 минут.  
  
## <a name="requirements"></a>Требования  
 Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="BlankReport"></a> 1. Создание пустого отчета, источника данных и набора данных  
  
> [!NOTE]  
>  В этом учебнике запрос содержит значения данных, поэтому отчету не требуется внешний источник данных. Использование этого типа внутренних данных отлично подходит в целях обучения, но делает запрос длинным. .  
  
#### <a name="to-create-a-blank-report"></a>Создание пустого отчета  
  
1.  Нажмите кнопку **Пуск**, наведите курсор на пункты **Все программы**, **Построитель отчетов Microsoft SQL Server 2012**и выберите пункт **Построитель отчетов**.  
  
    > [!NOTE]  
    >  Должно открыться диалоговое окно **Приступая к работе** . Если этого не произойдет, из меню для кнопки «Построитель отчетов» выберите команду **Создать**.  
  
2.  На левой панели диалогового окна **Приступая к работе** проверьте, выбран ли пункт **Новый отчет** .  
  
3.  На правой панели щелкните **Пустой отчет**.  
  
#### <a name="to-create-a-new-data-source"></a>Создание нового источника данных  
  
1.  В области данных отчета нажмите кнопку **Создать**и выберите **Источник данных**.  
  
2.  В `Name` введите: **ListDataSource**  
  
3.  Нажмите кнопку **Использовать соединение, внедренное в отчет**.  
  
4.  Убедитесь в том, что выбран тип соединения Microsoft SQL Server, а затем в поле **Строка подключения** введите: **Источник данных = \<имя_сервера>**  
  
     \<ServerName >, например Report001, указывает компьютер, на котором установлен экземпляр SQL Server Database Engine. Поскольку данные отчета не извлекаются из базы данных SQL Server, не нужно указывать имя базы данных. Для синтаксического анализа запроса используется база данных по умолчанию на указанном сервере.  
  
5.  Нажмите **Учетные данные**и введите учетные данные, необходимые для подключения к экземпляру ядра СУБД SQL Server.  
  
6.  Нажмите кнопку **ОК**.  
  
#### <a name="to-create-a-new-dataset"></a>Создание нового набора данных  
  
1.  В области данных отчета нажмите кнопку **Создать**и выберите **Набор данных**.  
  
2.  В `Name` введите: **ListDataset.**  
  
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
  
7.  Нажмите значок "Запуск", чтобы запустить запрос.  
  
     Результаты запроса — это данные, доступные для отображения в отчете.  
  
     ![Конструктор запросов](../../2014/tutorials/media/tutorial-querydesigner.png "Конструктор запросов")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="List"></a> 2. Добавление и настройка списка  
 Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предоставляют три шаблона области данных: таблицу, матрицу и список. Все эти шаблоны основаны на области данных табликса.  
  
 В данном учебнике вы будете использовать список для отображения сведений о территориальных продажах в отчете, напоминающем информационный бюллетень. Сведения группируются по территориям. Добавьте новую группу строк, в которой данные группируются по территориям, а затем удалите встроенную группу строк подробностей. Шаблон списка идеально подходит для создания отчетов произвольной формы. Дополнительные сведения см. в разделе [перечислены &#40;построитель отчетов и службы SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Для отчета используются размер бумаги Letter (8,5 X11) и поля шириной 1 дюйм. Страница отчета высотой более 9 дюймов или шириной более 6,5 дюймов может привести к формированию пустых страниц.  
  
#### <a name="to-add-a-list"></a>Добавление списка  
  
1.  На вкладке ленты **Вставка** в разделе **Области данных** щелкните **Список** , а затем перетащите список в текст отчета. Установите для списка высоту в 7 дюймов и ширину в 6,25 дюйма.  
  
2.  Щелкните внутри списка, щелкните правой кнопкой мыши на вершине списка и выберите **Свойства табликса**.  
  
     ![Добавление списка](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "Добавление списка")  
  
3.  В раскрывающемся списке **Имя набора данных** выберите пункт **ListDataset**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Щелкните правой кнопкой мыши внутри списка и выберите пункт **Свойства прямоугольной области**.  
  
     ![Команда "Свойства" прямоугольник](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "команда Свойства прямоугольника")  
  
6.  На вкладке **Общие** установите флажок **Вставить разрыв страницы после** .  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a>Добавление новой группы строк и удаление группы подробностей  
  
1.  На панели "Группы строк" щелкните правой кнопкой мыши группу подробностей, выберите пункт **Добавить группу**, а затем пункт **Родительская группа**.  
  
     ![Родительская группа команды](../../2014/tutorials/media/tutorial-parentgroupcommand.png "команда родительской группы")  
  
2.  В раскрывающемся списке выберите `[Territory].`  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     В список добавится столбец. Столбец содержит ячейку `[Territory].`  
  
4.  Щелкните правой кнопкой мыши столбец "Территория" в списке и выберите команду **Удалить столбцы**.  
  
     ![Удалить столбцы](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "удалить столбцы")  
  
5.  Выберите **Удалить только столбцы**.  
  
     ![Удаление столбцов-диалоговое окно](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "диалоговое окно «Удаление столбцов»")  
  
6.  На панели "Группы строк" щелкните правой кнопкой мыши группу **Подробности** , выберите пункт **Удалить группу**.  
  
     ![Удаление группы сведений](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "удаление группы сведений")  
  
7.  Щелкните **Удалить только группу**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Graphics"></a> 3. Добавление графических элементов  
 Одно из преимуществ использования области списка данных заключается в возможности добавлять в любом месте такие элементы отчета, как прямоугольники и текстовые поля, не ограничиваясь табличным макетом. Внешний вид отчета улучшается благодаря добавлению графических элементов (прямоугольника с цветной заливкой).  
  
#### <a name="to-add-graphic-elements-to-the-report"></a>Добавление графических элементов в отчет  
  
1.  На **вставить** вкладку ленты, нажмите кнопку **прямоугольник**, а затем перетащите прямоугольник в верхний левый угол списка. Установите высоту прямоугольника 7 дюймов и ширину 1 дюйм.  
  
2.  Щелкните правой кнопкой мыши прямоугольник, затем выберите пункт **Свойства прямоугольника**.  
  
3.  Перейдите на вкладку **Заливка** .  
  
4.  В раскрывающемся списке **Цвет заливки** нажмите **Другие цвета**и выберите **темно-серый** цвет.  
  
     ![Выберите цвет заливки](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "цвет заливки Select")  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 В левой стороне отчета теперь находится вертикальный графический элемент, состоящий из синевато-серого прямоугольника.  
  
##  <a name="Text"></a> 4. Добавление произвольного текста  
 Текстовое поле содержит статический текст, повторяемый на каждой странице отчета, а также поля данных.  
  
#### <a name="to-add-text-to-the-report"></a>Добавление текста в отчет  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  На вкладке **Вставка** ленты нажмите **Текстовое поле**и перетащите текстовое поле в верхний левый угол списка, но внутри добавленного ранее прямоугольника. Приближенно установите высоту текстового поля 3 дюйма и ширину 5 дюймов.  
  
3.  Поместите курсор в верхнюю часть текстового поля, а затем введите: **Информационный бюллетень для**.  
  
     ![Добавление текста заголовка бюллетеня](../../2014/tutorials/media/tutorial-newsletterfor.png "Добавление текста заголовка бюллетеня")  
  
    > [!NOTE]  
    >  Не забудьте вставить дополнительный пробел после слова «for». Пробел отделяет текст от поля, которое будет добавлено в следующем шаге.  
  
4.  Перетащите поле Territory в текстовое поле и поместите его после текста, введенного в шаге 3.  
  
     ![Добавить поля "Территория"](../../2014/tutorials/media/tutorial-addterritorialfield.png "поля \"Территория\" Добавить")  
  
5.  Выделите весь текст, щелкните его правой кнопкой мыши и выберите пункт **Свойства текста**.  
  
6.  Перейдите на вкладку **Шрифт** .  
  
7.  В списке **Шрифт** выберите **Times New Roman**; в списке **Размер** выберите **20 пт**, в списке **Цвет** выберите **Красный**.  
  
     ![Свойства текста](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "свойства текста")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Поместите курсор ниже текста, введенного в шаге 3 и введите: **Hello** .  
  
    > [!NOTE]  
    >  Не забудьте вставить дополнительный пробел после слова «Hello». Пробел отделяет текст от поля, которое будет добавлено в следующем шаге.  
  
10. Перетащите поле FullName в текстовое поле и поместите его после текста, введенного в шаге 9, а затем поставьте запятую (,).  
  
     ![Добавить поле полное имя](../../2014/tutorials/media/tutorial-addfullnamefield.png "добавьте полное имя поля")  
  
11. Выделите текст, добавленный в шагах 9 и 10, щелкните правой кнопкой мыши, а затем выберите **Свойства текста**.  
  
12. Перейдите на вкладку **Шрифт** .  
  
13. В списке **Шрифт** выберите **Times New Roman**; в списке **Размер** выберите **16 пт**, в списке **Цвет** выберите **Черный** .  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. Разместите курсор ниже текста, добавленного в шагах с 9 по 13, а затем скопируйте и вставьте следующий текст-заполнитель:  
  
    ```  
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque.   
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel.   
    ```  
  
16. Выделите текст, добавленный в шаге 15, щелкните правой кнопкой мыши, а затем выберите **Свойства текста**.  
  
17. Перейдите на вкладку **Шрифт** .  
  
18. В списке **Шрифт** выберите **Arial**, в списке **Размер** выберите **10 пт**, в списке **Цвет** выберите **Черный**.  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Добавление текста бюллетеня](../../2014/tutorials/media/tutorial-newslettertext.png "Добавление текста бюллетеня")  
  
20. Поместите курсор ниже текста, вставленного в шаге 15, а затем введите: **Поздравляем, ваш общий объем продаж из** .  
  
    > [!NOTE]  
    >  Не забудьте вставить дополнительный пробел после слова «of». Пробел отделяет текст от поля, которое будет добавлено в следующем шаге.  
  
21. Перетащите поле Sales в текстовое поле, поместите его после текста, введенного в шаге 20, а затем поставьте восклицательный знак (!).  
  
22. Выделите поле «продажи», щелкните правой кнопкой мыши поле и нажмите кнопку **выражение**.  
  
23. В поле выражений измените выражение, включив функцию Sum следующим образом:  
  
    ```  
    =Sum(Fields!Sales.value)  
    ```  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Добавить выражение в поле продаж](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "добавить выражение в поле продаж")  
  
25. Выделите текст, добавленный в шагах с 20 по 23, щелкните правой кнопкой мыши, а затем выберите **Свойства текста**.  
  
26. Перейдите на вкладку **Шрифт** .  
  
27. В списке **Шрифт** выберите **Times New Roman**, в списке **Размер** выберите **16 пт**, в списке **Цвет** выберите **Красный**.  
  
28. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
29. Выберите `[Sum(Sales)]` и на вкладке **Главная** , в группе **Число** нажмите кнопку **Валюта** .  
  
     ![Добавить символ валюты](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "добавить символ валюты")  
  
30. Щелкните правой кнопкой текстовое поле с текстом "Щелкните, чтобы добавить заголовок", а затем нажмите кнопку **Удалить**.  
  
31. Выберите поле списка и с помощью клавиш со стрелками переместите его в верхнюю часть страницы.  
  
32. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 В отчете отображается статический текст, и каждая страница отчета содержит данные для определенной территории. Данные о продажах форматируются как денежные значения.  
  
 ![Предварительный просмотр бюллетеня](../../2014/tutorials/media/tutorial-newsletters.png "Предварительный просмотр бюллетеня")  
  
##  <a name="Table"></a> 5. Добавление таблицы для показа подробностей о продажах  
 Используйте мастер создания новой таблицы или матрицы, чтобы добавить таблицу в отчет произвольной формы. После завершения работы мастера добавьте вручную строку для итогов.  
  
#### <a name="to-add-a-table"></a>Добавление таблицы  
  
1.  На вкладке ленты **Вставка** в разделе **Области данных** выберите **Таблица**, а затем щелкните **Мастер таблиц**.  
  
2.  На странице «Выбор набора данных» выберите **ListDataset**.  
  
3.  Нажмите кнопку **Далее**.  
  
4.  На странице **Выравнивание полей** перетащите поле Product из раздела **Доступные поля** в **Значения**.  
  
5.  Повторите шаг 4 для SalesDate, Quantity и Sales. Поместите SalesDate ниже Product, Quantity ниже SalesDate, а Sales ниже SalesDate.  
  
6.  Нажмите кнопку **Далее**.  
  
7.  На странице **Выбор макета** можно просмотреть макет таблицы.  
  
     Таблица очень проста. Она состоит из пяти столбцов и не имеет групп строк или столбцов. Поскольку группы отсутствуют, недоступны варианты макета, связанные с группами. Далее в учебнике таблица будет обновлена вручную для добавления итога.  
  
8.  Нажмите кнопку **Далее**.  
  
9. На странице **Выбор стиля** панели **Стили** выберите **Сланец**.  
  
10. Нажмите кнопку **Готово**.  
  
11. Перетащите таблицу ниже текстового поля, добавленного в занятии 4.  
  
    > [!NOTE]  
    >  Убедитесь, что таблица находится внутри списка.  
  
12. Убедившись, что таблица выбрана, щелкните правой кнопкой мыши затем панель группы строк "Сведения", выберите пункт **Добавить итоговое значение**, нажмите **После**.  
  
     ![Добавление общего отчета](../../2014/tutorials/media/tutorial-addtotal.png "Добавление общего отчета")  
  
13. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Отчет отображает таблицу со сведениями о продажах и итогами.  
  
 ![Продаж в отчете](../../2014/tutorials/media/tutorial-reportsalestotals.png "итоги продаж в отчете")  
  
##  <a name="Format"></a> 6. Форматирование данных  
 Числовые данные форматируются как денежное значение, а даты — только как день и время.  
  
#### <a name="to-format-fields-table"></a>Форматирование таблицы с полями  
  
1.  Щелкните **Конструктор** для переключения в режим конструктора.  
  
2.  Выберите ячейки таблицы, которые содержат `[Sum(SalesSales)]` , и на вкладке **Главная** в группе **Число** нажмите кнопку **Валюта** .  
  
     ![Добавить символ валюты в сумму продаж](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "добавить символ валюты в сумму продаж")  
  
3.  Щелкните ячейку, содержащую `[SalesDate]` , и в группе **Число** выберите **Дата**из раскрывающегося списка.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Теперь отчет содержит форматированные данные и более удобен для чтения.  
  
 ![Форматировать продаж в отчете](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "форматирования продаж в отчете")  
  
##  <a name="Save"></a> 7. Сохранение отчета  
 Отчеты можно сохранять на сервере отчетов, в библиотеке SharePoint или на компьютере. Вы также можете экспортировать отчет в разные форматы, например в Word или в PDF, запустив отчет и выбрав формат в меню **Экспорт** .  
  
 В данном учебнике предусмотрено сохранение отчета на сервере отчетов. Если нет доступа к серверу отчетов, сохраните отчет на компьютере.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Сохранение отчета на сервере отчетов  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Нажмите кнопку **Последние сайты и серверы**.  
  
3.  Выберите или введите имя сервера отчетов, для которого существует разрешение на сохранение отчетов.  
  
     Появится сообщение «Соединение с сервером отчетов». После того как соединение установлено, пользователю представляется содержимое папки, заданной администратором сервера отчетов как место по умолчанию для отчетов.  
  
4.  В `Name`, замените имя по умолчанию на **SalesInformationByTerritory**.  
  
5.  Нажмите кнопку **Сохранить**.  
  
 Отчет будет сохранен на сервере отчетов. Имя сервера отчетов, с которым установлено соединение, будет отображено в строке состояния в нижней части окна.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Сохранение отчета на компьютере  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Перейдите на **Рабочий стол**, откройте папку **Мои документы**или **Мой компьютер**и перейдите в папку, в которую нужно сохранить отчет.  
  
3.  В `Name`, замените имя по умолчанию на **SalesInformationByTerritory**.  
  
4.  Нажмите кнопку **Сохранить**.  
  
##  <a name="Line"></a> 8. Добавление строки в отдельные области отчета (необязательно)  
 Добавление строки в отдельные области редактирования и подробностей отчета.  
  
#### <a name="to-add-a-line"></a>Добавление линии  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  На вкладке ленты **Вставка** в области **Элементы отчета** щелкните **Линия**.  
  
3.  Проведите линию ниже поля произвольного текста, добавленного в занятии 4.  
  
4.  Щелкните линию.  
  
5.  Перейдите на вкладку **Главная** .  
  
6.  В области **Контур** выберите ширину **4,5** пт, цвет выберите **Красный**.  
  
     ![Добавление линии в отчет](../../2014/tutorials/media/tutorial-reportwithline.png "Добавление линии в отчет")  
  
##  <a name="Visualization"></a> 9. (Необязательно) Добавление отображения сводных данных  
 С помощью прямоугольников можно управлять подготовкой отчетов к просмотру. Поместите круговую диаграмму и гистограмму в прямоугольник, чтобы отчет был правильно подготовлен к просмотру.  
  
#### <a name="to-add-a-rectangle"></a>Добавление прямоугольника  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  На вкладке ленты **Вставка** в области **Элементы отчета** выберите **Прямоугольник**, а затем перетащите прямоугольник в список справа от таблицы. Установите ширину прямоугольника 2 дюйма и высоту 4 дюйма.  
  
3.  Выровняйте верхний край прямоугольника с верхним краем таблицы.  
  
#### <a name="to-add-a-pie-chart"></a>Добавление круговой диаграммы  
  
1.  На вкладке **Вставка** ленты в области **Визуализации данных** нажмите **Диаграмма** , затем — **Мастер диаграмм**.  
  
2.  На странице «Выбор набора данных» выберите **ListDataset**, а затем нажмите кнопку **Далее**.  
  
3.  Нажмите кнопку **Круговая диаграмма**, а затем кнопку **Далее**.  
  
4.  На странице "Размещение полей диаграммы" перетащите поле Product в **Категории**.  
  
5.  Перетащите поле Quantity в **значения**, а затем нажмите кнопку **Далее**.  
  
6.  На странице **Выбор стиля** панели **Стили** выберите **Сланец**.  
  
7.  Нажмите кнопку **Готово**.  
  
8.  Измените размеры диаграммы, показанной в верхнем левом углу отчета, установив высоту 1 1/2 дюйма и ширину 2 дюйма.  
  
9. Перетащите диаграмму в прямоугольник.  
  
     ![Добавление круговой диаграммы](../../2014/tutorials/media/tutorial-addpiechart.png "добавьте круговую диаграмму")  
  
10. Правой кнопкой мыши щелкните заголовок диаграммы, затем нажмите **Свойства заголовка диаграммы**.  
  
11. В **свойства заголовка диаграммы** диалоговое окно, в текст заголовка, введите: **Проданные объемы товаров**.  
  
12. Перейдите на вкладку **Шрифт** и в списке **Размер** выберите **10пт**.  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-column-chart"></a>Добавление гистограммы  
  
1.  На вкладке **Вставка** ленты в области **Визуализации данных** нажмите **Диаграмма** , затем — **Мастер диаграмм**.  
  
2.  На странице **Выбор набора данных** нажмите **ListDataset**, затем нажмите кнопку **Далее**.  
  
3.  Выберите **Столбец**, а затем нажмите кнопку **Далее**.  
  
4.  На странице «размещение полей диаграммы» перетащите поле Product **категории**.  
  
5.  Перетащите поле Sales в **Значения** , а затем нажмите кнопку **Далее**.  
  
     Значения отображаются по вертикальной оси.  
  
6.  На странице **Выбор стиля** панели **Стили** выберите **Сланец**.  
  
7.  Нажмите кнопку **Готово**.  
  
     Гистограмма добавляется в верхний левый угол отчета.  
  
8.  Измените размеры диаграммы, установив ширину 2 дюйма и высоту 2 дюйма.  
  
9. Перетащите диаграмму внутрь прямоугольника ниже круговой диаграммы.  
  
     ![Добавить столбец диаграммы](../../2014/tutorials/media/tutorial-addcolumnchart.png "добавить столбец диаграммы")  
  
10. Правой кнопкой мыши щелкните заголовок диаграммы, затем нажмите **Свойства заголовка**.  
  
11. В **свойства заголовка диаграммы** диалоговое окно, в текст заголовка, введите: **Продажи товаров**.  
  
12. Нажмите вкладку **Шрифт** , в списке **Размер** выберите **10 пт**и нажмите **ОК**.  
  
13. На диаграмме щелкните правой кнопкой мыши вертикальную ось, а затем снимите флажок **Показывать название оси**.  
  
14. Повторите пункт 13 для горизонтальной оси.  
  
15. Щелкните правой кнопкой мыши условные обозначения и выберите команду **Удалить условные обозначения**.  
  
    > [!NOTE]  
    >  После удаления заголовков осей и условных обозначений становится удобнее читать диаграммы малого размера.  
  
 ![Изменение названий диаграмм и удаление названия оси](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "Изменение названий диаграмм и удаление названия оси")  
  
#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a>Проверка местонахождения диаграмм внутри прямоугольника  
  
1.  Щелкните ранее добавленный в этом уроке прямоугольник.  
  
     Свойство `Name` на панели «Свойства» показывает имя прямоугольника.  
  
     ![Имя прямоугольника](../../2014/tutorials/media/tutorial-rectanglename.png "имя прямоугольника")  
  
2.  Щелкните круговую диаграмму.  
  
3.  В **свойства** области, убедитесь, что `Parent` свойство содержит имя прямоугольника.  
  
     ![Родительского свойства для круговой диаграммы](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "родительского свойства для круговой диаграммы")  
  
4.  Нажмите гистограмму и повторите пункты 2 и 3.  
  
    > [!NOTE]  
    >  Если диаграммы не находятся внутри прямоугольника, то не отображаются вместе в подготовленном к просмотру отчете.  
  
#### <a name="to-make-the-charts-the-same-size"></a>Придание одинаковых размеров диаграммам  
  
1.  Щелкните круговую диаграмму, нажмите клавишу Ctrl, а затем щелкните гистограмму.  
  
2.  Выделив обе диаграммы, щелкните правой кнопкой мыши, укажите **Макет**и выберите команду **Установить ту же ширину**.  
  
     ![Сделать ширины диаграмме одинаковыми](../../2014/tutorials/media/tutorial-makechartssamewidth.png "сделать ширины диаграмме одинаковыми")  
  
    > [!NOTE]  
    >  Элемент, который вы щелкнули сначала, задает ширину для всех выбранных элементов.  
  
3.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Теперь отчет содержит сводные данные о продажах в круговых диаграммах и гистограммах.  
  
 ![Руководства, отчета в свободной форме SSRS](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS учебника, отчета в свободной форме")  
  
## <a name="more-information"></a>Дополнительные сведения  
 Дополнительные сведения о списках см. в разделе [таблицы, матрицы и списки &#40;построитель отчетов и службы SSRS&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [перечислены &#40;построитель отчетов и службы SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [области данных Табликса Области &#40;построитель отчетов и службы SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), и [ячейки области данных Табликса, строк и столбцов &#40;построитель отчетов&#41; и службы SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
 Дополнительные сведения о конструкторах запросов см. в разделах [Конструкторы запросов (построитель отчетов)](../../2014/reporting-services/query-designers-report-builder.md) и [Пользовательский интерфейс текстового конструктора запросов (построитель отчетов)](report-data/text-based-query-designer-user-interface-report-builder.md).  
  
## <a name="see-also"></a>См. также  
 [Учебники по &#40;построитель отчетов&#41;](report-builder-tutorials.md)   
 [Построитель отчетов в SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  

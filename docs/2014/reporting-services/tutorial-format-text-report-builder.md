---
title: Учебник. Форматирование текста (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc58232ed3025063fb329392b58895ed667465f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098900"
---
# <a name="tutorial-format-text-report-builder"></a>Учебник. Форматирование текста (построитель отчетов)
  В этом учебнике приведено описание различных способов форматирования текста. После настройки пустого отчета с источником данных и набором данных выберите разделы, которые необходимо изучить.  
  
 На приведенном далее рисунке показан отчет, похожий на тот, который будет в итоге создан.  
  
 ![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")  
  
 На одном из этапов будет намеренно допущена ошибка с целью проиллюстрировать, почему именно она является ошибкой. После этого ошибка будет исправлена для достижения желаемого эффекта.  
  
 Улучшенная версия отчета, созданного в этом учебнике, доступна в качестве образца отчета в построителе отчетов [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Дополнительные сведения о загрузке этого и других образцов отчетов см. в разделе [Образцы отчетов построителя отчетов](https://go.microsoft.com/fwlink/?LinkId=184851).  
  
##  <a name="BackToTop"></a>Что вы узнаете  
  
### <a name="set-up-the-report"></a>Настройка отчета  
 1. [Создание пустого отчета с источником данных и набором данных](#CreateReport)  
  
 2. [Добавление поля в область конструктора отчетов (неправильным способом, затем правильным способом)](#AddField)  
  
 3. [Добавление таблицы в отчет область конструктора](#AddTable)  
  
### <a name="pick-and-choose"></a>Выбор разделов  
 [Добавление гиперссылки в отчет](#AddHyperlink)  
  
 [Поворот текста в отчете](#RotateText)  
  
 [Отображение текста с форматированием HTML](#FormatHTML)  
  
 [Формат валюты](#FormatCurrency)  
  
 [Сохранение отчета](#Save)  
  
 Предполагаемое время для выполнения заданий данного учебника: 20 минут  
  
## <a name="requirements"></a>Требования  
 Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="CreateReport"></a>Создание пустого отчета с источником данных и набором данных  
  
#### <a name="to-create-a-blank-report"></a>Создание пустого отчета  
  
1.  Нажмите **кнопку Пуск**, укажите пункт **программы**, выберите [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]пункт **Построитель отчетов**, а затем щелкните **Построитель отчетов**.  
  
    > [!NOTE]  
    >  Должно открыться диалоговое окно **Приступая к работе** . Если этого не произойдет, из меню для кнопки «Построитель отчетов» выберите команду **Создать**.  
  
2.  На левой панели диалогового окна **Приступая к работе** проверьте, выбран ли пункт **Новый отчет** .  
  
3.  На правой панели щелкните **Пустой отчет**.  
  
#### <a name="to-create-a-data-source"></a>Создание источника данных  
  
1.  В области данных отчета нажмите кнопку **создать**, а затем выберите **источник данных**.  
  
2.  В поле **Имя** введите **TextDataSource**  
  
3.  Нажмите кнопку **Использовать соединение, внедренное в отчет**.  
  
4.  Убедитесь в том, что выбран тип соединения Microsoft SQL Server, а затем в поле **Строка подключения** введите **Data Source = \<имя_сервера>**.  
  
    > [!NOTE]  
    >  Выражение \<ServerName>, например Report001, указывает компьютер, на котором установлен экземпляр ядро СУБД SQL Server. Для этого учебника не требуется специальных данных. Необходимо только соединение с базой данных [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Если соединение с источником данных в списке **Соединения с источниками данных**уже есть, выберите его и переходите к следующему этапу, "Создание набора данных". Дополнительные сведения см. в разделе [Альтернативные способы создания подключения к данным &#40;построитель отчетов&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a>Создание набора данных  
  
1.  В области данных отчета нажмите кнопку **создать**, а затем выберите **набор данных**.  
  
2.  Убедитесь в том, что источником данных является **TextDataSource**.  
  
3.  В поле **Имя** введите **TextDataset**.  
  
4.  Убедитесь, что выбран тип запроса **Текст** , и нажмите кнопку **Конструктор запросов**.  
  
5.  Нажмите кнопку **Изменить как текст**.  
  
6.  На панель запроса вставьте следующий запрос:  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  Чтобы запустить запрос, нажмите кнопку "Выполнить" ( **!** ).  
  
     Результаты запроса — это данные, доступные для отображения в отчете.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="AddField"></a>Добавление поля в отчет область конструктора  
 Когда необходимо добавить поле из набора данных в отчет, пользователю может показаться, что можно просто перетащить его непосредственно в область конструктора. В этом упражнении будет показано, почему этот способ не работает и что нужно делать вместо этого.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a>Добавление поля в отчет (и получение неправильного результата)  
  
1.  Перетащите поле **FullName** из области данных отчета в область конструктора.  
  
     Построитель отчетов создает текстовое поле с выражением в нем, которое представляется \<как expr>.  
  
2.  Нажмите кнопку **Запустить**.  
  
     Обратите внимание, что существует только одна запись, **Фернандо Росс (**, которая в алфавитном порядке является первой записью в запросе. Поле не повторяется и не показывает другие записи.  
  
3.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
4.  Выберите выражение \<expr> в текстовом поле.  
  
5.  На панели "Свойства" напротив свойства **Значение** видно следующее (если панель "Свойства" не видна, на вкладке **Вид** установите флажок **Свойства**):  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     Функция `First` создана для извлечения только первого значения в поле, именно это и было сделано.  
  
     В результате перетаскивания поля непосредственно в область конструктора было создано текстовое поле. Текстовые поля сами по себе не являются областями данных, поэтому они не отображают данные из набора данных отчета. Текстовые поля в областях данных, такие как таблицы, матрицы и списки, не отображают данные.  
  
6.  Выберите текстовое поле (если выражение выбрано, нажмите клавишу ESC для выбора текстового поля) и нажмите клавишу DELETE.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a>Добавление поля в отчет (и получение правильного результата)  
  
1.  На ленте на вкладке **Вставка** в области **Области данных** выберите **Список**. Щелкните область конструктора и перетащите курсор мыши, чтобы создать прямоугольник шириной 2 дюйма и высотой один дюйм.  
  
2.  Перетащите поле **FullName** из области данных отчета в поле списка.  
  
     В этот раз построитель отчетов создает текстовое поле с выражением `[FullName]` .  
  
3.  Нажмите кнопку **Запустить**.  
  
     Обратите внимание, что в этот раз поле повторяется и показывает все записи запроса.  
  
4.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
5.  Выберите выражение в текстовом поле.  
  
6.  На панели "Свойства" у свойства **Значение** вы увидите следующее:  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     Чтобы отобразить данные из набора данных, перетащите текстовое поле в область списка данных.  
  
7.  Выберите поле списка и нажмите клавишу DELETE.  
  
##  <a name="AddTable"></a>Добавление таблицы в отчет область конструктора  
 Создайте таблицу, чтобы получить место для размещения гиперссылок и повернутого текста.  
  
#### <a name="to-add-a-table-to-the-report"></a>Добавление таблицы в отчет  
  
1.  В меню **Вставка** выберите пункт **Таблица**, а затем выберите пункт **Мастер таблиц**.  
  
2.  На странице **Выбор набора данных** мастера создания таблицы или матрицы щелкните **выбрать существующий набор данных в этом отчете или общий набор данных**, а затем щелкните **TextDataset (в этом отчете)** и нажмите кнопку **Далее**.  
  
3.  На странице **Размещение полей** перетащите поля **территория**, **LinkText**и **Product** в **группы строк**, перетащите поле **Sales** в **значения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице **Выбор макета** снимите флажок **Развернуть/свернуть группы** , чтобы можно было увидеть всю таблицу, а затем нажмите кнопку **Далее**.  
  
5.  На странице **Выбор стиля** щелкните элемент **содержание**и нажмите кнопку **Готово**.  
  
6.  Перетащите таблицу так, чтобы она была ниже блока заголовка.  
  
7.  Нажмите кнопку **Запустить**.  
  
     Таблица выглядит правильно, однако имеет две итоговые строки. Для поля **LinkText** не требуется строка итогов.  
  
8.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
9. Щелкните правой кнопкой мыши текстовое поле, содержащее `[LinkText]`, и выберите пункт **разбить ячейки**.  
  
10. Выберите пустую `[LinkText]` ячейку под ячейкой, а затем нажмите и удерживайте клавишу Shift и выберите две ячейки справа: ячейка **итога** в столбце **продукт** и `[Sum(Sales)]` ячейка в столбце **продажи** .  
  
11. Выбрав эти три ячейки, щелкните правой кнопкой мыши одну из этих ячеек и выберите команду **Удалить строку**.  
  
12. Нажмите кнопку **Запустить**.  
  
##  <a name="AddHyperlink"></a>Добавление гиперссылки в отчет  
 В этом разделе будет показано добавление гиперссылки в текст таблицы из предыдущего раздела.  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a>Добавление гиперссылки на отчет  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните правой кнопкой мыши ячейку, содержащую `[LinkText]`, и выберите пункт **Свойства текстового поля**.  
  
3.  В поле **Свойства текстового поля** выберите **действие**.  
  
4.  Щелкните **Переход к URL-адресу**.  
  
5.  В поле **Выбор URL-адреса** щелкните **[URL-адрес]**, а затем нажмите кнопку **ОК**.  
  
6.  Обратите внимание, что текст ничем не отличается. Необходимо сделать так, чтобы текст выглядел как текст ссылки.  
  
7.  Выберите `[LinkText]`.  
  
8.  В разделе **Шрифт** на вкладке **Главная** нажмите кнопку **Подчеркнутый** , а затем щелкните стрелку раскрывающегося списка рядом с кнопкой **Цвет** и выберите **синий цвет**.  
  
9. Нажмите кнопку **Запустить**.  
  
     Теперь текст выглядит как ссылка.  
  
10. Щелкните ссылку. Если компьютер подключен к Интернету, браузер откроет раздел справки построителя отчетов.  
  
##  <a name="RotateText"></a>Поворот текста в отчете  
 В этом разделе будет показано вращение выбранного текста таблицы из предыдущих разделов.  
  
#### <a name="to-rotate-text"></a>Вращение текста  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните ячейку, содержащую `[Territory].`  
  
3.  На вкладке **Главная** в разделе **Шрифт** нажмите кнопку **Полужирный** .  
  
4.  Если панель свойств не открыта, перейдите на вкладку **Вид** и установите флажок **Свойства** .  
  
5.  На панели свойств откройте свойство WritingMode.  
  
    > [!NOTE]  
    >  Если свойства на панели свойств упорядочены по категориям, свойство WritingMode относится к категории **Локализация** . Убедитесь, что выбрана ячейка, а не текст. WritingMode является свойством текстового поля, а не текста.  
  
6.  В списке щелкните **Rotate270**.  
  
7.  На вкладке **Главная** в разделе **абзац** щелкните кнопки **середина** и **Центральная** , чтобы нахождение текста в центре ячейки как по вертикали, так и по горизонтали.  
  
8.  Нажмите кнопку "Запустить" ( **!** ).  
  
 Теперь текст в ячейке `[Territory]` располагается вертикально снизу вверх.  
  
##  <a name="FormatHTML"></a>Отображение текста с форматированием HTML  
  
#### <a name="to-display-text-formatted-as-html"></a>Отображение текста в формате HTML  
  
1.  Щелкните **Конструктор** для переключения в режим конструктора.  
  
2.  На вкладке **Вставка** нажмите **Текстовое поле**, а затем в области конструктора щелкните и перетащите указатель мыши так, чтобы создать текстовое поле под таблицей примерно десять сантиметров шириной и семь с половиной сантиметров высотой.  
  
3.  Скопируйте этот текст и вставьте его в текстовое поле:  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  Выберите весь текст в текстовом поле.  
  
     Это свойство текста, а не текстового поля, поэтому в одном текстовом поле может находиться как простой текст, так и HTML-разметка для обозначения стилей.  
  
5.  Щелкните правой кнопкой мыши весь выделенный текст и выберите пункт **Свойства текста**.  
  
6.  На странице **Общие** в разделе **тип разметки**щелкните **HTML — интерпретировать HTML-теги как стили**.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Нажмите кнопку "Выполнить" ( **!** ) для предварительного просмотра отчета.  
  
 Текст в текстовом поле отображается как заголовок, абзац и маркированный список.  
  
##  <a name="FormatCurrency"></a>Формат валюты  
  
#### <a name="to-format-numbers-as-currency"></a>Форматирование чисел в формате валюты  
  
1.  Щелкните **Конструктор** для переключения в режим конструктора.  
  
2.  Щелкните верхнюю ячейку таблицы, содержащую `[Sum(Sales)]`, и, удерживая клавишу SHIFT, нажмите нижнюю ячейку таблицы, содержащую `[Sum(Sales)]`.  
  
3.  На вкладке **Главная** в группе **Число** нажмите кнопку **Валюта** .  
  
4.  Используемых На вкладке **Главная** в группе **число** нажмите кнопку **Стили заполнителя** и нажмите кнопку **выборка значений** , чтобы увидеть, как будут отформатированы числа.  
  
5.  На вкладке **Главная** в группе **Число** нажмите два раза кнопку **Уменьшить разрядность** , чтобы суммы в долларах отображались без центов (необязательно).  
  
6.  Нажмите кнопку "Выполнить" ( **!** ) для предварительного просмотра отчета.  
  
 Теперь отчет содержит форматированные данные и более удобен для чтения.  
  
##  <a name="Save"></a>Сохранение отчета  
 Отчеты можно сохранять на сервере отчетов, в библиотеке SharePoint или на компьютере.  
  
 В данном учебнике предусмотрено сохранение отчета на сервере отчетов. Если нет доступа к серверу отчетов, сохраните отчет на компьютере.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Сохранение отчета на сервере отчетов  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Нажмите кнопку **Последние сайты и серверы**.  
  
3.  Выберите или введите имя сервера отчетов, для которого существует разрешение на сохранение отчетов.  
  
     Появится сообщение «Соединение с сервером отчетов». После того как соединение установлено, пользователю представляется содержимое папки, заданной администратором сервера отчетов как место по умолчанию для отчетов.  
  
4.  В поле **Имя**замените имя по умолчанию на произвольное имя.  
  
5.  Выберите команду **Сохранить**.  
  
 Отчет будет сохранен на сервере отчетов. Имя сервера отчетов, с которым установлено соединение, будет отображено в строке состояния в нижней части окна.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Сохранение отчета на компьютере  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Перейдите на **Рабочий стол**, откройте папку **Мои документы**или **Мой компьютер**и перейдите в папку, в которую нужно сохранить отчет.  
  
3.  В поле **Имя**замените имя по умолчанию на произвольное имя.  
  
4.  Выберите команду **Сохранить**.  
  
## <a name="next-steps"></a>Next Steps  
 Существует множество способов форматирования текста в построитель отчетов [руководстве. Создание отчета в свободной форме &#40;построитель отчетов&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) содержит дополнительные примеры.  
  
## <a name="see-also"></a>См. также:  
 [Учебники &#40;построитель отчетов&#41;](report-builder-tutorials.md)   
 [Форматирование элементов отчета (построитель отчетов и службы SSRS)](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Построитель отчетов в SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  

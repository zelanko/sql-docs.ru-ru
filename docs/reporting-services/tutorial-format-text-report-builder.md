---
title: Учебник. Форматирование текста (построитель отчетов) | Документация Майкрософт
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 090729625991e3a1aaa6fb1ada3012a15ff20dce
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "63043044"
---
# <a name="tutorial-format-text-report-builder"></a>Учебник. Форматирование текста (построитель отчетов)

В этом учебнике приведено описание различных способов форматирования текста в отчете [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] с разбивкой на страницы. Вы можете поэкспериментировать с различными форматами. 

После настройки пустого отчета с источником данных и набором данных вы можете выбрать форматы, которые необходимо изучить. На приведенном далее рисунке показан отчет, похожий на тот, который будет в итоге создан.  
  
![report-build-format-report](../reporting-services/media/report-build-format-report.png) 
  
На одном из этапов будет намеренно допущена ошибка с целью проиллюстрировать, почему именно она является ошибкой. После этого ошибка будет исправлена для достижения желаемого эффекта.  
    
Предполагаемое время для выполнения заданий данного учебника: 20 минут  
  
## <a name="requirements"></a>Требования  
Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/prerequisites-for-tutorials-report-builder.md).  
  
## <a name="create-a-blank-report-with-a-data-source-and-dataset"></a><a name="CreateReport"></a>Создание пустого отчета с источником данных и набором данных  
  
### <a name="to-create-a-blank-report"></a>Создание пустого отчета  
  
1.  [Запустите построитель отчетов](../reporting-services/report-builder/start-report-builder.md) с компьютера, веб-портала [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] или сервера в режиме интеграции с SharePoint.  
  
    Откроется диалоговое окно **Создать отчет или набор данных** .  
  
    Если диалоговое окно **Новый отчет или набор данных** не появилось, в меню **Файл** выберите команду **Создать**.  
 
2.  На левой панели диалогового окна **Приступая к работе** проверьте, выбран ли пункт **Новый отчет** .  
  
3.  На правой панели щелкните **Пустой отчет**.  
  
### <a name="to-create-a-data-source"></a>Создание источника данных  
  
1.  В области данных отчета нажмите кнопку **Создать** > **Источник данных**.  

    Если область **данных отчета** не видна, на вкладке **Вид** установите флажок **Данные отчета**.
  
2.  В поле **Имя** введите **TextDataSource**  
  
3.  Нажмите кнопку **Использовать соединение, внедренное в отчет**.  
  
4.  Убедитесь в том, что выбран тип соединения Microsoft SQL Server, а затем в поле **Строка подключения** введите: `Data Source = <servername>`  
  
    > [!NOTE]  
    > Выражение `<servername>`, например Report001, указывает компьютер, на котором установлен экземпляр компонента SQL Server Database Engine. Для этого учебника не требуется специальных данных. Необходимо только подключение к базе данных SQL Server. Если соединение с источником данных в списке **Соединения с источниками данных**уже есть, выберите его и переходите к следующему этапу, "Создание набора данных". Дополнительные сведения см. в разделе [Альтернативные способы создания подключения к данным &#40;построитель отчетов&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-create-a-dataset"></a>Создание набора данных  
  
1.  В области данных отчета щелкните **Создать** > **Набор данных**.  
  
2.  Убедитесь в том, что источником данных является **TextDataSource**.  
  
3.  В поле **Имя** введите **TextDataset**.  
  
4.  Убедитесь, что выбран тип запроса **Текст** , и нажмите кнопку **Конструктор запросов**.  
  
5.  Нажмите кнопку **Изменить как текст**.  
  
6.  На панель запроса вставьте следующий запрос:  

    > [!NOTE]  
    > В этом учебнике запрос уже содержит значения данных, поэтому внешний источник данных не требуется. В связи с этим запрос получается весьма длинным. В рабочей среде запрос не будет содержать данные. Этот запрос содержит данные только в учебных целях.  
  
    ```  
    SELECT CAST('2015-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Install Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Report Builder in SQL Server' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2015-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Reporting Services (SSRS)' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  Чтобы запустить запрос, нажмите кнопку "Выполнить" ( **!** ).  
  
    Результаты запроса — это данные, доступные для отображения в отчете.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

9.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="add-a-field-to-the-report-design-surface"></a><a name="AddField"></a>Добавление поля в область конструктора отчетов  
Когда необходимо добавить поле из набора данных в отчет, пользователю может показаться, что можно просто перетащить его непосредственно в область конструктора. В этом упражнении будет показано, почему этот способ не работает и что нужно делать вместо этого.  
  
### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a>Добавление поля в отчет (и получение неправильного результата)  
  
1.  Перетащите поле **FullName** из области данных отчета в область конструктора.  
  
    Построитель отчетов создает текстовое поле с выражением, представленным как `<Expr>`.  
  
2.  Нажмите кнопку **Запустить**.  
  
    Есть только одна запись **Fernando Ross**, которая по алфавиту является первой записью в запросе. Поле не повторяется и не показывает другие записи.  
  
3.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
4.  Выберите выражение `<Expr>` в текстовом поле.  
  
5.  На панели "Свойства" напротив свойства **Значение** видно следующее (если панель "Свойства" не видна, на вкладке **Вид** установите флажок **Свойства**):  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
    Функция `First` создана для извлечения только первого значения в поле, именно это и было сделано.  
  
    В результате перетаскивания поля непосредственно в область конструктора было создано текстовое поле. Текстовые поля сами по себе не являются областями данных, поэтому они не отображают данные из набора данных отчета. Текстовые поля в областях данных, такие как таблицы, матрицы и списки, не отображают данные.  
  
6.  Выберите текстовое поле (если выражение выбрано, нажмите клавишу ESC для выбора текстового поля) и нажмите клавишу DELETE.  
  
### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a>Добавление поля в отчет (и получение правильного результата)  
  
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
  
    Чтобы отобразить данные из текстового поля набора данных, перетащите это поле в область данных списка.  
  
7.  Выберите поле списка и нажмите клавишу DELETE.  
  
## <a name="add-a-table-to-the-report-design-surface"></a><a name="AddTable"></a>Добавление таблицы в область конструктора отчетов  
Создайте таблицу, чтобы получить место для размещения гиперссылок и повернутого текста.   
  
1.  На вкладке **Вставка** выберите пункт **Таблица** > **Мастер таблиц**.  
  
2.  На странице **Выбор набора данных** мастера создания таблицы или матрицы щелкните **Выбрать существующий набор данных в этом отчете или общий набор данных** > **TextDataset (в этом отчете)**  > **Далее**.  
  
3.  На странице **Размещение полей** перетащите поля **Territory**, **LinkText**и **Product** в **Группы строк**, поле **Sales** — в **Значения**, а затем нажмите кнопку **Далее**.  

    ![report-builder-text-arrange-fields](../reporting-services/media/report-builder-text-arrange-fields.png)
  
4.  На странице **Выбор макета** снимите флажок **Развернуть или свернуть группы** , чтобы была видна вся таблица, и нажмите кнопку **Далее**. 
  
5.  Нажмите кнопку **Готово**.  
  
6.  Нажмите кнопку **Запустить**.  
  
    Таблица выглядит правильно, однако имеет две итоговые строки. Столбцу **LinkText** не нужна итоговая строка.  
    
    ![report-builder-format-2-totals](../reporting-services/media/report-builder-format-2-totals.png)
  
8.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
9. Выберите ячейку **Итого** в столбце **LinkText**, а затем справа от нее выберите, удерживая нажатой клавишу SHIFT, две ячейки: пустую ячейку в столбце **Product** и ячейку `[Sum(Sales)]` в столбце **Sales**.  
  
11. Выбрав три ячейки, щелкните правой кнопкой мыши одну из них и выберите пункт **Удалить строки**.  

    ![report-builder-format-delete-rows](../reporting-services/media/report-builder-format-delete-rows.png)
  
12. Нажмите кнопку **Запустить**.  

    Теперь имеется только одна строка "Итого".
    
    ![report-builder-format-one-total](../reporting-services/media/report-builder-format-one-total.png)
  
## <a name="add-a-hyperlink-to-the-report"></a><a name="AddHyperlink"></a>Добавление гиперссылки в отчет  
В этом разделе будет показано добавление гиперссылки в текст таблицы из предыдущего раздела.  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните правой кнопкой мыши ячейку, содержащую `[LinkText]`, и выберите пункт **Свойства текстового поля**.  
  
3.  На вкладке **Действия** выберите команду **Перейти по URL-адресу**.  
  
5.  В поле **Выбор URL-адреса** щелкните **[URL]** , а затем нажмите кнопку **ОК**.  
  
6.  Обратите внимание, что текст ничем не отличается. Необходимо сделать так, чтобы текст выглядел как текст ссылки.  
  
7.  Выберите `[LinkText]`.  
  
8.  На вкладке **Главная** в разделе **Шрифт** выберите **Подчеркнутый** и измените **Цвет** на **Синий**.  
  
9. Нажмите кнопку **Запустить**.  
  
    Теперь текст выглядит как ссылка.  
    
    ![report-builder-format-hyperlink](../reporting-services/media/report-builder-format-hyperlink.png)
  
10. Щелкните ссылку. Если компьютер подключен к Интернету, браузер откроет раздел справки построителя отчетов.  
  
## <a name="rotate-text-in-the-report"></a><a name="RotateText"></a>Вращение текста в отчете  
В этом разделе будет показано вращение выбранного текста таблицы из предыдущих разделов.  
 
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните ячейку, содержащую `[Territory].`  
  
3.  На вкладке **Главная** в разделе **Шрифт** нажмите кнопку **Полужирный** .  
  
4.  Если панель свойств не открыта, перейдите на вкладку **Вид** и установите флажок **Свойства** .  
  
5.  Найдите свойство WritingMode на панели "Свойства" и измените его значение с **По умолчанию** на **Rotate270**.  
 
    > [!NOTE]  
    > Если свойства на панели свойств упорядочены по категориям, свойство WritingMode относится к категории **Локализация** . Убедитесь, что выбрана ячейка, а не текст. WritingMode является свойством текстового поля, а не текста.  

    ![report-builder-select-territory-cell](../reporting-services/media/report-builder-select-territory-cell.png)
   
6.  На вкладке **Главная** в разделе **Абзац** нажмите кнопки **Середина** и **Центр** для размещения текста по центру ячейки в горизонтальном и вертикальном направлениях.  
  
8.  Нажмите кнопку "Запустить" ( **!** ).  
  
Теперь текст в ячейке `[Territory]` располагается вертикально снизу вверх.  

![report-builder-format-rotate-270](../reporting-services/media/report-builder-format-rotate-270.png)

## <a name="format-currency"></a><a name="FormatCurrency"></a>Форматирование значения валюты  
  
1.  Щелкните **Конструктор** для переключения в режим конструктора.  
  
2.  Щелкните верхнюю ячейку таблицы, содержащую `[Sum(Sales)]`, и, удерживая клавишу SHIFT, нажмите нижнюю ячейку таблицы, содержащую `[Sum(Sales)]`.  
  
3.  На вкладке **Главная** в группе **Число** нажмите кнопку **Валюта**.  
  
4.  Если в качестве региональных настроек компьютера выбран "Английский (США)", текстом образца по умолчанию будет [ **$12,345.00**]\(необязательно). Если значение валюты не отображается, в группе **Числа** щелкните **Стили заполнителя** > **Образцы значений**.  

    ![report-builder-placeholder-value-button](../reporting-services/media/report-builder-placeholder-value-button.png)
  
5.  На вкладке **Главная** в группе **Число** нажмите два раза кнопку **Уменьшить разрядность** , чтобы суммы в долларах отображались без центов (необязательно).  
  
6.  Нажмите кнопку "Выполнить" ( **!** ) для предварительного просмотра отчета.  
  
Теперь отчет содержит форматированные данные и более удобен для чтения.  

![report-build-format-report](../reporting-services/media/report-build-format-report.png)
    
## <a name="displaying-text-with-html-formatting"></a><a name="FormatHTML"></a>Отображение текста в формате HTML  
  
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
  
4.  Перетащите нижний край текстового поля так, чтобы в нем помещался весь текст. Обратите внимание на то, что рабочая область конструирования увеличивается при перетаскивании.

5. Выберите весь текст в текстовом поле.  
  
5.  Щелкните правой кнопкой мыши весь выделенный текст и выберите пункт **Свойства текста**.  
  
    Это свойство текста, а не текстового поля, поэтому в одном текстовом поле может находиться как простой текст, так и HTML-разметка для обозначения стилей.  
  
6.  На вкладке **Общее** в группе **Тип разметки**щелкните **HTML — интерпретировать HTML-теги как стили**.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Нажмите кнопку "Выполнить" ( **!** ) для предварительного просмотра отчета.  
  
Текст в текстовом поле отображается как заголовок, абзац и маркированный список.  
  
![report-builder-format-html](../reporting-services/media/report-builder-format-html.png)

## <a name="save-the-report"></a><a name="Save"></a>Сохранение отчета  
Отчеты можно сохранять на сервере отчетов, в библиотеке SharePoint или на компьютере.  
  
В данном учебнике предусмотрено сохранение отчета на сервере отчетов. Если нет доступа к серверу отчетов, сохраните отчет на компьютере.  
  
### <a name="to-save-the-report-on-a-report-server"></a>Сохранение отчета на сервере отчетов  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Нажмите кнопку **Последние сайты и серверы**.  
  
3.  Выберите или введите имя сервера отчетов, для которого существует разрешение на сохранение отчетов.  
  
    Появится сообщение «Соединение с сервером отчетов». После того как соединение установлено, пользователю представляется содержимое папки, заданной администратором сервера отчетов как место по умолчанию для отчетов.  
  
4.  В поле **Имя**замените имя по умолчанию на произвольное имя.

5.  Выберите команду **Сохранить**.  
  
Отчет будет сохранен на сервере отчетов. Имя сервера отчетов, с которым установлено соединение, будет отображено в строке состояния в нижней части окна.  
  
### <a name="to-save-the-report-on-your-computer"></a>Сохранение отчета на компьютере  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Перейдите на **Рабочий стол**, откройте папку **Мои документы**или **Мой компьютер**и перейдите в папку, в которую нужно сохранить отчет.  
  
3.  В поле **Имя**замените имя по умолчанию на произвольное имя. 
  
4.  Выберите команду **Сохранить**.  

## <a name="next-steps"></a>Next Steps

В построителе отчетов предусмотрено несколько способов форматирования текста. [Учебник. Создание отчета в свободной форме](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) содержит дополнительные примеры.  

[Руководства по построителю отчетов](../reporting-services/report-builder-tutorials.md) 
[Форматирование элементов отчета](../reporting-services/report-design/formatting-report-items-report-builder-and-ssrs.md)  
[Построитель отчетов в SQL Server](../reporting-services/report-builder/report-builder-in-sql-server-2016.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).

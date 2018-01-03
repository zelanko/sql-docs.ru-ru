---
title: "Занятие 3: Анализ и визуализация данных | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 7fe670f3-5e62-43ef-97eb-b9af54df9128
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a47e9d2b2bec007af27b8e8ce26d6a6c6f67c3f
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>Занятие 3: Анализ и визуализация данных

В этой статье является частью учебника для разработчиков SQL по использованию R в SQL Server.

На этом занятии предстоит просмотреть образец данных, а затем создать некоторые графики с помощью функций R. Эти функции R уже включены в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Можно вызывать функции R из [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="review-the-data"></a>Проверка данных

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Поэтому сначала внимательно просмотрите образец данных, если это еще не сделано.

В исходном наборе данных идентификаторы такси и записи о поездках были предоставлены в отдельных файлах. Тем не менее, чтобы облегчить использование образца данных, двумя исходными наборами данных были присоединены по столбцам _medallion_, _hack\_лицензии_, и _раскладки\_ DateTime_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**
  
-   В столбце _medallion_ представлены уникальные идентификационные номера такси.
  
-   _Hack\_лицензии_ столбец содержит номер соглашения драйвер такси (анонимизированы).
  
**Записи о поездках и оплате**
  
-   Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.
  
-   Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.
  
-   Последние три столбца можно использовать для различных задач машинного обучения.  _Совет\_сумма_ столбец содержит непрерывные числовые значения и можно использовать в качестве **метка** столбец для анализа регрессии. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. _Совет\_класса_ столбец содержит несколько **метки класса** и поэтому может использоваться как метка задачах классификации несколькими классами.
  
    В этом пошаговом руководстве демонстрируется только задача двоичной классификации. Вы можете самостоятельно попробовать создать модели для двух других задач машинного обучения: регрессии и многоклассовой классификации.
  
-   Значения, используемые для меток столбцов основаны на _совет\_сумма_ столбца, с помощью этих бизнес-правила:
  
    |Имя производного столбца|Правило|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-plots-using-r-in-t-sql"></a>Создание диаграммы с помощью R в T-SQL

Так как визуализация является эффективным средством для представления распределения данных и выбросов, в R имеется много пакетов для визуализации данных. Стандартный дистрибутив R с открытым исходным кодом также включает множество функций для создания гистограмм, точечных диаграмм, блочных диаграмм и других типов диаграмм для анализа данных.

Изображения обычно создаются в R с помощью устройства R для вывода графики. Выходные данные этого устройства можно записать и сохранить изображение с типом данных **varbinary** для отрисовки в приложении. Изображения можно также сохранять в любом из поддерживаемых форматов файлов (JPG, PDF и т. д.).

В этом разделе вы научитесь работать с каждым типом выходных данных с использованием хранимых процедур. Общий процесс выглядит следующим образом:

- Создание хранимой процедуры для создания построения R, как данные типа varbinary

- Создание графика и сохраните его в файл изображения

- Используйте хранимую процедуру для преобразования двоичных отобразить данные в файл JPG или PDF

### <a name="create-the-stored-procedure-plothistogram"></a>Создайте хранимую процедуру PlotHistogram

1. Чтобы создать диаграмму, используйте `rxHistogram`, один из расширенных функциях R в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], строится на основе данных из гистограммы [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Чтобы вызывать функцию R было проще, вы включите ее в хранимую процедуру _PlotHistogram_.

    В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], откройте новый **запроса** окна.

2. В базе данных с данными учебник Создайте процедуру с помощью этой инструкции:

    ```SQL
    CREATE PROCEDURE [dbo].[PlotHistogram]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =  
      N'SELECT tipped FROM nyctaxi_sample'  
      EXECUTE sp_execute_external_script @language = N'R',  
                                         @script = N'  
       image_file = tempfile();  
       jpeg(filename = image_file);  
       #Plot histogram  
       rxHistogram(~tipped, data=InputDataSet, col=''lightgreen'',   
       title = ''Tip Histogram'', xlab =''Tipped or not'', ylab =''Counts'');  
       dev.off();  
       OutputDataSet <- data.frame(data=readBin(file(image_file, "rb"), what=raw(), n=1e6));  
       ',  
       @input_data_1 = @query  
       WITH RESULT SETS ((plot varbinary(max)));  
    END
    GO
    ```

    При необходимости замените имя таблицы в коде на нужное.
  
    -   Переменная `@query` определяет текст запроса (`'SELECT tipped FROM nyctaxi_sample'`), который передается в скрипт R в качестве аргумента входной переменной `@input_data_1`.
  
    -   Скрипт R достаточно прост: в нем определяется переменная R (`image_file`) для хранения изображения, а затем вызывается функция `rxHistogram` для создания диаграммы.
  
    -   Устройство R устанавливается в состояние **off**.
  
        При использовании высокоуровневой команды построения диаграммы в среде R открывается графическое окно, называемое *устройством*. Вы можете изменить размер, цвета и другие аспекты окна либо выключить устройство, если производится запись в файл или выходные данные обрабатываются каким-либо иным способом.
  
    -   Графический объект R сериализуется в кадр данных R для вывода.

### <a name="generate-the-graphics-data-and-save-to-file"></a>Создание графических данных и сохранить в файл

Эта хранимая процедура возвращает изображение в виде потока данных varbinary, которые, очевидно, нельзя просмотреть напрямую. Однако вы можете использовать служебную программу **bcp** для получения данных varbinary и сохранения их в виде файла изображения на клиентском компьютере.
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]выполните следующую инструкцию:
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **Результаты**
    
    *построения*
    *0xFFD8FFE000104A4649...*
  
2.  Откройте окно командной строки PowerShell и выполните следующую команду, указав в качестве аргументов соответствующие имя экземпляра, имя базы данных, имя пользователя и учетные данные:
  
     ```
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  <database name>  -U <user name> -P <password>
     ```

    > [!NOTE]
    > Параметры для bcp учитывается регистр.
  
3.  Если подключение успешно установлено, появится запрос на ввод дополнительных сведений о формате графического файла. Нажимайте клавишу ВВОД, чтобы принять значения по умолчанию, за исключением указанных ниже изменений.
  
    -   Для **длины префикса диаграммы поля**введите значение 0.
  
    -   Введите **Y** , если необходимо сохранить выходные параметры для повторного использования в будущем.
  
    ```
    Enter the file storage type of field plot [varbinary(max)]:
    Enter prefix-length of field plot [8]: 0
    Enter length of field plot [0]:
    Enter field terminator [none]:
  
    Do you want to save this format information in a file? [Y/n]
    Host filename [bcp.fmt]:
    ```
  
    **Результаты**
    
    ```
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > Если сохранить сведения о формате в файл (bcp.fmt), программа **bcp** создаст определение формата, которое можно применять к схожим командам в дальнейшем, не получая запросы на задание параметров формата графического файла. Чтобы использовать файл формата, добавьте `-f bcp.fmt` в конец любой командной строки после аргумента пароля.
  
4.  Выходной файл будет создан в том же каталоге, в котором выполнялась команда PowerShell. Чтобы просмотреть диаграмму, просто откройте файл plot.jpg.
  
    ![Поездки на такси с чаевыми и без](media/rsql-devtut-tippedornot.jpg "Поездки на такси с чаевыми и без")  
  
### <a name="export-the-plot-data-to-a-viewable-file"></a>Экспорт данных диаграммы в файл для просмотра

Вывод построения R на двоичные данные типа может быть удобным для потребления приложениями, но это не очень полезен для анализу данных, которым необходим рисунка, отображаемого на этапе просмотра данных. Как правило, специалист по анализу создает несколько визуализаций, чтобы рассмотреть данные с разных сторон.

Для создания диаграмм для пользователей, можно использовать хранимую процедуру, которая создает выходные данные R в популярные форматы, такие как. JPG. PDF-файла, и. PNG. После того как хранимая процедура создаст графические данные, просто откройте файл, чтобы отобразить диаграмму.

1. Создать новую хранимую процедуру _PlotInOutputFiles_, демонстрирует способ записи гистограммы, scatterplots и другие графические R для. JPG и. Формат PDF.

    В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], откройте новый **запроса** окна и вставить в следующем примере [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PlotInOutputFiles]  
    AS  
    BEGIN  
      SET NOCOUNT ON;  
      DECLARE @query nvarchar(max) =  
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'  
      EXECUTE sp_execute_external_script @language = N'R',  
      @script = N'  
       # Set output directory for files and check for existing files with same names   
        mainDir <- ''C:\\temp\\plots''  
        dir.create(mainDir, recursive = TRUE, showWarnings = FALSE)  
        setwd(mainDir);  
        print("Creating output plot files:", quote=FALSE)
        
        # Open a jpeg file and output histogram of tipped variable in that file.  
        dest_filename = tempfile(pattern = ''rHistogram_Tipped_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.jpg'',sep="")  
        print(dest_filename, quote=FALSE);  
        jpeg(filename=dest_filename);  
        hist(InputDataSet$tipped, col = ''lightgreen'', xlab=''Tipped'',   
            ylab = ''Counts'', main = ''Histogram, Tipped'');  
         dev.off();  

        # Open a pdf file and output histograms of tip amount and fare amount.   
        # Outputs two plots in one row  
        dest_filename = tempfile(pattern = ''rHistograms_Tip_and_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=7);  
        par(mfrow=c(1,2));  
        hist(InputDataSet$tip_amount, col = ''lightgreen'',   
            xlab=''Tip amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram, Tip amount'', xlim = c(0,40), 100);  
        hist(InputDataSet$fare_amount, col = ''lightgreen'',   
            xlab=''Fare amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram,   
            Fare amount'',   
            xlim = c(0,100), 100);  
       dev.off();  
  
        # Open a pdf file and output an xyplot of tip amount vs. fare amount using lattice;  
        # Only 10,000 sampled observations are plotted here, otherwise file is large.  
        dest_filename = tempfile(pattern = ''rXYPlots_Tip_vs_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=4);  
        plot(tip_amount ~ fare_amount,   
            data = InputDataSet[sample(nrow(InputDataSet), 10000), ],   
            ylim = c(0,50),   
            xlim = c(0,150),   
            cex=.5,   
            pch=19,   
            col=''darkgreen'',    
            main = ''Tip amount by Fare amount'',   
            xlab=''Fare Amount ($)'',   
            ylab = ''Tip Amount ($)'');   
        dev.off();',  
     @input_data_1 = @query  
     END
    ```
  
    -   Выходные данные запроса SELECT в хранимой процедуре сохраняются в кадре данных R по умолчанию ( `InputDataSet`). После этого можно вызывать различные функции построения диаграмм R для создания графических файлов.
  
        Встроенный скрипт R по большей части представляет собой параметры для этих графических функций, таких как `plot` и `hist`.
  
    -   Все файлы сохраняются в локальной папке _C:\temp\Plots\\_. Папка назначения определяется аргументами, предоставляемыми скрипту R в рамках хранимой процедуры.  Чтобы поменять папку назначения, измените значение переменной `mainDir`.
  
2.  Выполните инструкцию, чтобы создать хранимую процедуру.

    ```SQL
    EXEC PlotInOutputFiles
    ```

    **Результаты**
    
    ```
    STDOUT message(s) from external script:
    [1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 
    
    C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]
    
    C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
    ```

    Числа в именах файлов случайным образом, не получить ошибку при попытке записи в существующий файл.

3. Чтобы просмотреть график, откройте папку назначения и просмотрите файлы, которые были созданы с помощью кода R в хранимые процедуры.

    + Файл `rHistogram_Tipped.jpg` показывает количество приема-передачи, попавших совет сравнение приема-передачи, попавших без подсказки. (Это гистограмма — так же, как один, созданный на предыдущем шаге).

    + Файл `rHistograms_Tip_and_Fare_Amount.pdf` показывает распределение суммы совет, строиться по тариф авиакомпании суммы.
    
    ![Гистограмма, показывающая tip_amount и fare_amount](media/rsql-devtut-tipamtfareamt.PNG "Гистограмма, показывающая tip_amount и fare_amount")

    + Файл `rXYPlots_Tip_vs_Fare_Amount.pdf` содержит scatterplot с тариф авиакомпании по оси x и подсказка сумму по оси y.

    ![Сумма совет отображаются над тариф авиакомпании сумма](media/rsql-devtut-tipamtbyfareamt.PNG "сумма совет отображаются над тариф авиакомпании сумма")

2.  Чтобы вывести файлы в другую папку, измените значение переменной `mainDir` в скрипте R, встроенном в хранимую процедуру. Скрипт также можно изменить так, чтобы данные выводились в других форматах, в большее количество файлов и т. д.

## <a name="next-lesson"></a>Следующее занятие

[Занятие 4: Создание компонентов данных, с помощью T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 2: Импорт данных в SQL Server с помощью PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

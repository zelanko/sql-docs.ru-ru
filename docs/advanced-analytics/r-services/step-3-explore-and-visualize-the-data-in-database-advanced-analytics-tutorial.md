---
title: "Шаг&#160;3. Анализ и визуализация данных (учебник по дополнительным аналитическим функциям в базе данных) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 7fe670f3-5e62-43ef-97eb-b9af54df9128
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Шаг&#160;3. Анализ и визуализация данных (учебник по дополнительным аналитическим функциям в базе данных)
Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. В этом шаге вы изучите образец данных, а затем создадите ряд диаграмм с помощью функций R. Эти функции R уже включены в службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. В этом пошаговом руководстве вы поупражняетесь в вызове функций R из [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## Изучение данных  
Для начала немного изучите образец данных, если вы этого еще не делали.  
  
В исходном наборе данных идентификаторы такси и записи о поездках были предоставлены в отдельных файлах. Однако, чтобы образец данных было удобнее использовать, исходные наборы данных были объединены по столбцам _medallion_, _hack_license_ и _pickup_datetime_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.  
  
**Идентификаторы такси**  
  
-   В столбце _medallion_ представлены уникальные идентификационные номера такси.  
  
-   В столбце _hack_license_ содержатся номера лицензий таксистов (без указания имен).  
  
**Записи о поездках и оплате**  
  
-   Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.  
  
-   Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.  
  
-   Последние три столбца можно использовать для различных задач машинного обучения.  Столбец _tip_amount_ содержит непрерывный ряд числовых значений и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip_class_ содержит несколько **меток классов** и поэтому может использоваться в качестве метки для задач многоклассовой классификации.  
  
    В этом пошаговом руководстве демонстрируется только задача двоичной классификации. Вы можете самостоятельно попробовать создать модели для двух других задач машинного обучения: регрессии и многоклассовой классификации.  
  
-   Все значения, используемые для столбцов меток, основаны на столбце _tip_amount_ с применением следующих бизнес-правил:  
  
    |Имя производного столбца|Правило|  
    |-|-|  
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|  
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|  
  
## Создание диаграмм с помощью языка R в T-SQL  
Так как визуализация является эффективным средством для представления распределения данных и выбросов, в R имеется много пакетов для визуализации данных. Стандартный дистрибутив R с открытым исходным кодом также включает множество функций для создания гистограмм, точечных диаграмм, блочных диаграмм и других типов диаграмм для анализа данных.  
  
Изображения обычно создаются в R с помощью устройства R для вывода графики. Выходные данные этого устройства можно записать и сохранить изображение с типом данных **varbinary** для отрисовки в приложении. Изображения можно также сохранять в любом из поддерживаемых форматов файлов (JPG, PDF и т. д.).  
  
В этом разделе вы научитесь работать с каждым типом выходных данных с использованием хранимых процедур.  
  
-   Сохранение диаграмм с типом данных varbinary  
  
-   Сохранение диаграмм в файлах (JPG, PDF) на сервере  
  
### Сохранение диаграмм с типом данных varbinary  
Вы используете `rxHistogram`, одну из расширенных функций R, предоставляемую службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], для построения гистограммы на основе данных, полученных из запроса [!INCLUDE[tsql](../../includes/tsql-md.md)]. Чтобы вызывать функцию R было проще, вы включите ее в хранимую процедуру _PlotHistogram_.  
  
Эта хранимая процедура возвращает изображение в виде потока данных varbinary, которые, очевидно, нельзя просмотреть напрямую. Однако вы можете использовать служебную программу **bcp** для получения данных varbinary и сохранения их в виде файла изображения на клиентском компьютере.  
  
##### Создание хранимой процедуры PlotHistogram  
  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] откройте новое окно запроса.  
  
2.  Выберите базу данных, предназначенную для пошагового руководства, и создайте процедуру с помощью приведенной ниже инструкции.  
  
    ```  
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
  
    -   Графический объект R сериализуется в кадр данных R для вывода. Это временное решение в версии CTP3.  
  
##### Вывод данных varbinary в доступный для просмотра графический файл  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выполните следующую инструкцию:  
  
    ```  
    EXEC [dbo].[PlotHistogram]  
    ```  
  
**Результаты**  
  
*plot*  
*0xFFD8FFE000104A4649...*  
  
2.  Откройте окно командной строки PowerShell и выполните следующую команду, указав в качестве аргументов соответствующие имя экземпляра, имя базы данных, имя пользователя и учетные данные:  
  
    ```  
    bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  <database name>  -U <user name> -P <password>  
  
    ```  
  
    > [!NOTE]  
    > В параметрах команды **bcp** учитывается регистр.  
  
3.  Если подключение успешно установлено, появится запрос на ввод дополнительных сведений о формате графического файла. Нажимайте клавишу ВВОД, чтобы принять значения по умолчанию, за исключением указанных ниже изменений.  
  
    -   Для **длины префикса диаграммы поля** введите значение 0.  
  
    -   Введите **Y**, если необходимо сохранить выходные параметры для повторного использования в будущем.  
  
    ```  
    Enter the file storage type of field plot [varbinary(max)]:  
    Enter prefix-length of field plot [8]: 0  
    Enter length of field plot [0]:  
    Enter field terminator [none]:  
  
    Do you want to save this format information in a file? [Y/n]  
    Host filename [bcp.fmt]:  
  
    ```  
  
**Результаты**  
  
*Начинается копирование...*  
*Скопировано строк: 1.*  
*Размер сетевого пакета (байт): 4096*  
*Время (мс) Всего: 3922   В среднем: (0,25 строк в секунду)*  
   
> [!TIP]  
 > Если сохранить сведения о формате в файл (bcp.fmt), программа **bcp** создаст определение формата, которое можно применять к схожим командам в дальнейшем, не получая запросы на задание параметров формата графического файла. Чтобы использовать файл формата, добавьте `-f bcp.fmt` в конец любой командной строки после аргумента пароля.  
  
4.  Выходной файл будет создан в том же каталоге, в котором выполнялась команда PowerShell. Чтобы просмотреть диаграмму, просто откройте файл plot.jpg.  
  
    ![taxi trips with and without tips](../../advanced-analytics/r-services/media/rsql-devtut-tippedornot.jpg "taxi trips with and without tips")  
  
### Сохранение диаграмм в файлах (JPG, PDF) на сервере  
Вывод диаграммы R в двоичный тип данных может быть удобным, если диаграмма должна использоваться приложениями, но не очень полезен для специалиста по анализу данных, которому требуется отрисованная диаграмма на этапе изучения данных. Как правило, специалист по анализу создает несколько визуализаций, чтобы рассмотреть данные с разных сторон.  
  
Для формирования более удобных для просмотра диаграмм можно использовать хранимую процедуру, которая создает выходные данные R в популярных форматах, таких как JPG, PDF и PNG. После того как хранимая процедура создаст графические данные, просто откройте файл, чтобы отобразить диаграмму.  
  
В этом шаге вы создадите хранимую процедуру _PlotInOutputFiles_, которая демонстрирует использование функций построения диаграмм R для создания гистограмм, точечных и других диаграмм в форматах JPG и PDF. Графические данные сохраняются в локальных файлах, то есть в папке в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##### Создание хранимой процедуры PlotInOutputFiles  
  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] откройте новое окно запроса и вставьте приведенную ниже инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
    ```  
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
  
    -   Выходные данные запроса SELECT в хранимой процедуре сохраняются в кадре данных R по умолчанию (`InputDataSet`). После этого можно вызывать различные функции построения диаграмм R для создания графических файлов.  
  
        Встроенный скрипт R по большей части представляет собой параметры для этих графических функций, таких как `plot` и `hist`.  
  
    -   Все файлы сохраняются в локальной папке _C:\temp\Plots\\_.  
  
        Папка назначения определяется аргументами, предоставляемыми скрипту R в рамках хранимой процедуры.  Чтобы поменять папку назначения, измените значение переменной `mainDir`.  
  
2.  Выполните инструкцию, чтобы создать хранимую процедуру.  
  
  
##### Создание графических файлов  
  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните следующий запрос SQL:  
  
    ```  
    EXEC PlotInOutputFiles  
  
    ```  
  
**Результаты**  
  
*Сообщения STDOUT из внешнего скрипта:*  
*[1] Создание выходных файлов диаграммы:[1]* *C:\\\temp\\\plots\\\rHistogram_Tipped_18887f6265d4.jpg[1]* *C:\\\temp\\\plots\\\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]* *C:\\\temp\\\plots\\\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf*  
  
2.  Откройте папку назначения и просмотрите файлы, которые были созданы кодом R в хранимой процедуре. (Числа в именах файлов создаются случайным образом.)  
  
*  rHistogram_Tipped_*nnnn*.jpg: показывает число поездок, за которые были получены чаевые (1), в сравнении с числом поездок без чаевых (0). Эта гистограмма очень похожа на ту, которая была создана в предыдущем шаге.  
  
*  rHistograms_Tip_and_Fare_Amount_*nnnn*.pdf: показывает распределение значений в столбцах tip_amount и fare_amount.  
  
        ![histogram showing tip_amount and fare_amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtfareamt.PNG "histogram showing tip_amount and fare_amount")  
  
*  rXYPlots_Tip_vs_Fare_Amount_*nnnn*.pdf: точечная диаграмма с размером оплаты по оси x и размером чаевых по оси y.  
  
        ![tip amount plotted over fare amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtbyfareamt.PNG "tip amount plotted over fare amount")  
  
3.  Чтобы вывести файлы в другую папку, измените значение переменной `mainDir` в скрипте R, встроенном в хранимую процедуру.  
  
    Скрипт также можно изменить так, чтобы данные выводились в других форматах, в большее количество файлов и т. д.  
  
## Следующий шаг  
[Шаг 4. Создание характеристик данных с помощью T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## Предыдущий шаг  
[Шаг 2. Импорт данных в SQL Server с помощью PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## См. также:  
[Дополнительные аналитические функции в базе данных для разработчиков SQL (учебник)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Учебники по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  

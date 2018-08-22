---
title: Занятие 3 изучение и визуализация данных с помощью R и T-SQL (машинного обучения SQL Server) | Документация Майкрософт
description: Учебник, в котором показано, как внедрить R в SQL Server хранимых процедур и функций T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: cffbc00b5b3a3c1c8ab01e14319f3267e323022a
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393508"
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>Занятие 3: Анализ и визуализация данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит руководства для разработчиков SQL по использованию R в SQL Server.

На этом занятии будет изучите образец данных, а затем создадите ряд диаграмм с помощью [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) из [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и универсальный [Hist](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) функции в базовый R. Эти функции R уже включены в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Ключевой целью отображается способ вызова функций R из [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимых процедурах и сохранить результаты в форматах файлов приложения:

+ Создание хранимой процедуры с помощью **RxHistogram** для создания диаграммы R как данные типа varbinary. Используйте **bcp** Экспорт двоичного потока в файл изображения.
+ Создание хранимой процедуры с помощью **Hist** для создания графиков, сохранение результатов в качестве выходных данных JPG и PDF.

> [!NOTE]
> Так как визуализация является эффективным средством для понимания того, форма представления данных и распространение, R предоставляет широкий набор функций и пакетов для создания гистограмм, точечных диаграмм, блочных диаграмм и других диаграммах исследования данных. Изображения, с помощью устройства R для вывода графики, который можно записать и сохранить как, обычно создаются в R **varbinary** тип данных для подготовки к просмотру в приложении. Также можно сохранить образы в любом из форматов файлов поддержки (. JPG. PDF и т. д.).

## <a name="review-the-data"></a>Просмотрите данные

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Поэтому сначала внимательно изучите образец данных, если у вас еще нет.

В исходном наборе данных идентификаторы такси и записи о поездках были предоставлены в отдельных файлах. Тем не менее, чтобы упростить использование демонстрационных данных, исходные наборы данных были объединены по столбцам _medallion_, _hack\_лицензии_, и _pickup\_ DateTime_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**
  
-   В столбце _medallion_ представлены уникальные идентификационные номера такси.
  
-   _Hack\_лицензии_ столбец содержит драйвера такси номера лицензий (таксистов).
  
**Записи о поездках и оплате**
  
-   Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.
  
-   Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.
  
-   Последние три столбца можно использовать для различных задач машинного обучения. _Совет\_сумма_ столбец содержит непрерывные числовые значения и можно использовать в качестве **метка** столбец для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. _Совет\_класс_ столбца имеет несколько **меток классов** и поэтому может использоваться как метка для задач многоклассовой классификации.
  
    В этом пошаговом руководстве демонстрируется только задача двоичной классификации. Вы можете самостоятельно попробовать создать модели для двух других задач машинного обучения: регрессии и многоклассовой классификации.
  
-   Все значения, используемые для столбцов меток основаны на _совет\_сумма_ столбца, с помощью этих бизнес-правила:
  
    |Имя производного столбца|Правило|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Создание хранимой процедуры, использование rxHistogram для построения этих данных

Чтобы создать график, используйте [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), одно из расширенных функций R, входящих в [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). Этот шаг отображает гистограммы на основе данных из [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Эту функцию можно включить в хранимой процедуре, **PlotHistogram**.

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], в обозревателе объектов щелкните правой кнопкой мыши **TaxiNYC_Sample** базы данных, разверните **программирования**, а затем разверните **хранимые процедуры** для просмотра процедуры, созданные в занятии 2.

2. Щелкните правой кнопкой мыши **PlotHistogram** и выберите **изменить** для просмотра исходного кода. Чтобы выполнить эту процедуру, чтобы вызвать **rxHistogram** на данные, содержащиеся в столбце скошенные таблицы nyctaxi_sample.

3. При необходимости в качестве упражнения для обучения создайте собственную копию этой хранимой процедуры, с помощью следующего примера. Откройте новое окно запроса и вставьте в следующий скрипт, чтобы создать хранимую процедуру, которая отображает гистограмму. В этом примере называется **PlotHistogram2** во избежание коллизий между именами предварительно существующую процедуру.

    ```SQL
    CREATE PROCEDURE [dbo].[PlotHistogram2]
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

Хранимая процедура **PlotHistogram2** идентична существующей хранимой процедуры **PlotHistogram** созданные `RunSQL_SQL_Walkthrough.ps1` скрипта. 
  
+ Переменная `@query` определяет текст запроса (`'SELECT tipped FROM nyctaxi_sample'`), который передается в скрипт R в качестве аргумента входной переменной `@input_data_1`.
  
+ Скрипт R достаточно прост: переменную R (`image_file`) определяется для хранения образа, а затем **rxHistogram** функция вызывается для создания диаграммы.
  
+ Устройство R устанавливается **off** так, как при выполнении этой команды как внешний скрипт в SQL Server. Обычно в R, при использовании команды высокого уровня построения, R открывается графическое окно, называемое *устройства*. Вы можете изменить размер, цвета и другие аспекты окна либо выключить устройство, если производится запись в файл или выходные данные обрабатываются каким-либо иным способом.
  
+ Графический объект R сериализуется в кадр данных R для вывода.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Выполните хранимую процедуру и экспорт двоичных данных в файл изображения с помощью bcp

Эта хранимая процедура возвращает изображение в виде потока данных varbinary, которые, очевидно, нельзя просмотреть напрямую. Однако вы можете использовать служебную программу **bcp** для получения данных varbinary и сохранения их в виде файла изображения на клиентском компьютере.
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]выполните следующую инструкцию:
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **Результаты**
    
    *График*
    *0xFFD8FFE000104A4649...*
  
2.  Откройте командную строку PowerShell и выполните следующую команду, указав соответствующее имя экземпляра, имя базы данных, имя пользователя и учетные данные в качестве аргументов. Для тех, с помощью удостоверений Windows, можно заменить **- U** и **-P** с **-T**.
  
     ```text
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  TaxiNYC_Sample  -U <user name> -P <password>
     ```

    > [!NOTE]
    > Ключи для bcp учитывается регистр.
  
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
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Создание хранимой процедуры с помощью Hist и нескольких форматов выходных данных

Как правило обработке и анализу данных создает несколько визуализаций для получения представления о данных с различных точек зрения. В этом примере хранимая процедура использует функцию Hist для создания гистограммы, экспорта двоичные данные в популярных форматах, таких как. JPG. PDF-ФАЙЛ, и. PNG. 

1. Использовать существующую хранимую процедуру, **PlotInOutputFiles**, написать гистограмм, точечных и других графических средств R для. JPG и. Формат PDF. `RunSQL_SQL_Walkthrough.ps1` Создает **PlotInOutputFiles** и добавляет его в базе данных. Щелкните правой кнопкой мыши использовать **изменить** для просмотра исходного кода.

2. При необходимости в качестве упражнения для обучения, создайте собственную копию в процедуру в качестве **PlotInOutputFiles2**, с уникальным именем, чтобы избежать конфликта имен.

    В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], откройте новую **запроса** окно "и" Вставить ниже [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PlotInOutputFiles2]  
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
  
+ Выходные данные запроса SELECT в хранимой процедуре сохраняются в кадре данных R по умолчанию ( `InputDataSet`). После этого можно вызывать различные функции построения диаграмм R для создания графических файлов. Встроенный скрипт R по большей части представляет собой параметры для этих графических функций, таких как `plot` и `hist`.
  
+ Все файлы сохраняются в локальной папке _C:\temp\Plots\\_. Папка назначения определяется аргументами, предоставляемыми скрипту R в рамках хранимой процедуры.  Чтобы поменять папку назначения, измените значение переменной `mainDir`.

+ Чтобы вывести файлы в другую папку, измените значение переменной `mainDir` в скрипте R, встроенном в хранимую процедуру. Скрипт также можно изменить так, чтобы данные выводились в других форматах, в большее количество файлов и т. д.

### <a name="execute-the-stored-procedure"></a>Выполнение хранимой процедуры

Выполните следующую инструкцию, чтобы экспортировать двоичный отобразить данные в форматах PDF и JPEG.

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

Числа в именах файлов генерируются случайным образом, чтобы убедиться, что не отобразится сообщение об ошибке при попытке записи в существующий файл.

### <a name="view-output"></a>Просмотр выходных данных 

Чтобы просмотреть диаграмму, откройте папку назначения и просмотреть файлы, которые были созданы кодом R в хранимой процедуре.

1. Перейдите в папку, указанную в сообщении STDOUT (в примере это C:\temp\plots\)

2. Откройте `rHistogram_Tipped.jpg` для отображения количества поездок, которые были получены чаевые против поездок без чаевых. (Эта Гистограмма очень похожа на ту, которая была создана в предыдущем шаге).

3. Откройте `rHistograms_Tip_and_Fare_Amount.pdf` Чтобы просмотреть распределение сумм чаевых, строиться по сумм.
    
  ![Гистограмма, показывающая столбцах tip_amount и fare_amount](media/rsql-devtut-tipamtfareamt.PNG "Гистограмма, показывающая столбцах tip_amount и fare_amount")

4. Откройте `rXYPlots_Tip_vs_Fare_Amount.pdf` для просмотра Точечная диаграмма с тарифа на оси x, а также чаевых по оси y.

   ![Отложенный чаевых за сумма тарифа](media/rsql-devtut-tipamtbyfareamt.PNG "чаевых отображаются над сумма тарифа")

## <a name="next-lesson"></a>Следующее занятие

[Занятие 3: Создание функций данных с помощью T-SQL](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 1: Настройка демонстрационных данных о такси Нью-ЙОРКА](sqldev-download-the-sample-data.md)

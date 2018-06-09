---
title: Занятие 3 Просмотр и визуализация данных с помощью R и T-SQL (SQL Server машинного обучения) | Документы Microsoft
description: Руководство для внедрения в SQL Server R хранимые процедуры и функции T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 057d7d988fd6f7f5d490cbf30f06e83270438983
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250087"
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>Занятие 3: Анализ и визуализация данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника для разработчиков SQL по использованию R в SQL Server.

На этом занятии предстоит просмотреть образец данных, а затем создать некоторые графики с помощью [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) из [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и универсальный [Hist](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) функции в базовый R. Эти функции R уже включены в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Ключевая цель показан способ вызова функций R из [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимых процедурах и сохраните результаты в форматах файлов приложения:

+ Создание хранимой процедуры с помощью **RxHistogram** для создания построения R, как данные типа varbinary. Используйте **bcp** Экспорт двоичного потока в файл изображения.
+ Создание хранимой процедуры с помощью **Hist** для создания диаграммы, сохранение результатов в качестве выходных данных JPG и PDF.

> [!NOTE]
> Поскольку визуализация таких мощное средство для понимания данных фигуры и распространения, R предоставляет широкий набор функций и пакетов для создания гистограммы, точечных диаграмм, графиков поле и других диаграммах исследования данных. R обычно создает образы, используя устройство R для графического вывода, который можно записать и сохранить в качестве **varbinary** тип данных для подготовки к просмотру в приложении. Образы также можно сохранить в любом из форматов файлов поддержки (. JPG. PDF и т. д.).

## <a name="review-the-data"></a>Проверка данных

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Поэтому сначала внимательно просмотрите образец данных, если это еще не сделано.

В исходном наборе данных идентификаторы такси и записи о поездках были предоставлены в отдельных файлах. Тем не менее, чтобы облегчить использование образца данных, двумя исходными наборами данных были присоединены по столбцам _medallion_, _hack\_лицензии_, и _раскладки\_ DateTime_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**
  
-   В столбце _medallion_ представлены уникальные идентификационные номера такси.
  
-   _Hack\_лицензии_ столбец содержит номер соглашения драйвер такси (анонимизированы).
  
**Записи о поездках и оплате**
  
-   Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.
  
-   Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.
  
-   Последние три столбца можно использовать для различных задач машинного обучения. _Совет\_сумма_ столбец содержит непрерывные числовые значения и можно использовать в качестве **метка** столбец для анализа регрессии. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. _Совет\_класса_ столбец содержит несколько **метки класса** и поэтому может использоваться как метка задачах классификации несколькими классами.
  
    В этом пошаговом руководстве демонстрируется только задача двоичной классификации. Вы можете самостоятельно попробовать создать модели для двух других задач машинного обучения: регрессии и многоклассовой классификации.
  
-   Значения, используемые для меток столбцов основаны на _совет\_сумма_ столбца, с помощью этих бизнес-правила:
  
    |Имя производного столбца|Правило|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Создание хранимой процедуры с помощью rxHistogram представления данных

Чтобы создать диаграмму, используйте [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), один из расширенных функциях R в [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). Этот шаг отображает гистограммы на основе данных из [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Эту функцию можно включить в хранимой процедуре, **PlotHistogram**.

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в обозревателе объектов, щелкните правой кнопкой мыши **TaxiNYC_Sample** базы данных, разверните **программирования**, а затем разверните **хранимых процедур** для просмотра процедуры, созданный на занятии 2.

2. Щелкните правой кнопкой мыши **PlotHistogram** и выберите **изменить** для просмотра источника. Можно выполнить эту процедуру, чтобы вызвать **rxHistogram** на данные, содержащиеся в столбце скошенные nyctaxi_sample таблицы.

3. При необходимости, упражнения для обучения создайте собственную копию этой хранимой процедуры, показано в следующем примере. Откройте новое окно запроса и вставьте следующий скрипт, чтобы создать хранимую процедуру, которая отображает гистограммы. В этом примере называется **PlotHistogram2** во избежание конфликтов с существующие процедуры имен.

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

Хранимая процедура **PlotHistogram2** идентична существующей хранимой процедуры **PlotHistogram** созданные `RunSQL_SQL_Walkthrough.ps1` сценария. 
  
+ Переменная `@query` определяет текст запроса (`'SELECT tipped FROM nyctaxi_sample'`), который передается в скрипт R в качестве аргумента входной переменной `@input_data_1`.
  
+ R-скрипта очень прост: переменной R (`image_file`) определяется для снятия образа, а затем **rxHistogram** функция вызывается для создания графика.
  
+ Устройство R равно **off** так, как вы используете эту команду в качестве внешнего сценария, в SQL Server. Обычно в R, при использовании команды высокого уровня построения, R открывается окно графики, вызывается *устройства*. Вы можете изменить размер, цвета и другие аспекты окна либо выключить устройство, если производится запись в файл или выходные данные обрабатываются каким-либо иным способом.
  
+ Графический объект R сериализуется в кадр данных R для вывода.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Выполните хранимую процедуру и использовать bcp для экспорта двоичных данных в файл изображения

Эта хранимая процедура возвращает изображение в виде потока данных varbinary, которые, очевидно, нельзя просмотреть напрямую. Однако вы можете использовать служебную программу **bcp** для получения данных varbinary и сохранения их в виде файла изображения на клиентском компьютере.
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]выполните следующую инструкцию:
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **Результаты**
    
    *построения*
    *0xFFD8FFE000104A4649...*
  
2.  Откройте командную строку PowerShell и выполните следующую команду, указав соответствующее имя экземпляра, имя базы данных, имя пользователя и учетные данные в качестве аргументов. Для тех, с использованием удостоверения Windows, можно заменить **- U** и **-P** с **-T**.
  
     ```text
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  TaxiNYC_Sample  -U <user name> -P <password>
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
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Создание хранимой процедуры с использованием нескольких форматов вывода и Hist

Как правило специалисты по анализу данных создают несколько представлений данных, чтобы получить представление о данных с различных точек зрения. В этом примере хранимая процедура использует функцию Hist для создания гистограммы, таких как Экспорт двоичных данных в популярные форматы. JPG. PDF-файла, и. PNG. 

1. Использовать существующую хранимую процедуру **PlotInOutputFiles**, для создания гистограммы, scatterplots и другие графические R для. JPG и. Формат PDF. `RunSQL_SQL_Walkthrough.ps1` Создает **PlotInOutputFiles** и добавляет ее в базе данных. Щелкните правой кнопкой мыши использовать **изменить** для просмотра источника.

2. При необходимости в качестве упражнения для обучения, создайте собственную копию процедуры как **PlotInOutputFiles2**, с уникальным именем, чтобы избежать конфликта имен.

    В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], откройте новый **запроса** окна и вставить в следующем примере [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.
  
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

Выполните следующую инструкцию, чтобы экспортировать исходные двоичные данные в формате JPEG и PDF форматы файлов.

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

### <a name="view-output"></a>Просмотр выходных данных 

Чтобы просмотреть график, откройте папку назначения и просмотрите файлы, которые были созданы с помощью кода R в хранимые процедуры.

1. Перейдите в папку, указанную в сообщении STDOUT (в примере это C:\temp\plots\)

2. Откройте `rHistogram_Tipped.jpg` для отображения номера приема-передачи данных, есть совет сравнение приема-передачи, попавших без подсказки. (Это гистограмма — так же, как один, созданный на предыдущем шаге).

3. Откройте `rHistograms_Tip_and_Fare_Amount.pdf` Просмотр распределения сумм совет, строиться по тариф авиакомпании суммы.
    
  ![Гистограмма, показывающая tip_amount и fare_amount](media/rsql-devtut-tipamtfareamt.PNG "Гистограмма, показывающая tip_amount и fare_amount")

4. Откройте `rXYPlots_Tip_vs_Fare_Amount.pdf` для просмотра scatterplot с объемом тариф авиакомпании на оси x, а сумма совет по оси y.

   ![Сумма совет отображаются над тариф авиакомпании сумма](media/rsql-devtut-tipamtbyfareamt.PNG "сумма совет отображаются над тариф авиакомпании сумма")

## <a name="next-lesson"></a>Следующее занятие

[Занятие 4: Создание компонентов данных, с помощью T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 2: Подготовка учебника среды с помощью PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

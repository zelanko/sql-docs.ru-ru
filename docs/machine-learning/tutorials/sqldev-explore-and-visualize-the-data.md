---
title: Учебник по R и T-SQL. Анализ данных
description: Учебник с инструкциями по анализу и визуализации данных SQL Server с помощью функций R.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 03/03/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bc5434483fd6f63a73362fb42b1bd17aa749ebd3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757100"
---
# <a name="lesson-1-explore-and-visualize-the-data"></a>Урок 1. Анализ и визуализация данных
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта статья является частью учебника для разработчиков SQL с инструкциями по использованию R в SQL Server.

На этом шаге вы изучите образец данных, а затем создадите несколько диаграмм с помощью [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) из [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и универсальной функции [Hist](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) в базовом пакете R. Эти функции R уже включены в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Главная цель этого занятия — показать, как вызывать функции R из [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимых процедурах и сохранять результаты в форматах файлов приложения.

+ Создание хранимой процедуры с помощью **RxHistogram** для построения диаграммы R в виде данных типа varbinary. Использование **bcp** для экспорта двоичного потока в файл изображения.
+ Создание хранимой процедуры с помощью **Hist** для построения диаграммы и сохранения результатов в формате JPG и PDF.

> [!NOTE]
> Поскольку визуализация является мощным инструментом для понимания формы и распространения данных, R предоставляет ряд функций и пакетов для создания гистограмм, точечных диаграмм, блочных диаграмм и других типов диаграмм для исследования данных. Как правило, изображения в R создаются с помощью устройства R для вывода графики. Выходные данные можно записать и сохранить с типом данных **varbinary** для отрисовки в приложении. Изображения можно также сохранять в любом из поддерживаемых форматов файлов (JPG, PDF и т. д.).

## <a name="review-the-data"></a>Изучение данных

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Для начала немного изучите образец данных, если вы это еще не сделали.

В исходном общедоступном наборе данных идентификаторы такси и записи о поездках были предоставлены в отдельных файлах. Однако, чтобы образец данных было удобнее использовать, два исходных набора данных были объединены по столбцам _medallion_, _hack\_license_, и _pickup\_datetime_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**
  
-   В столбце _medallion_ представлены уникальные идентификационные номера такси.
  
-   В столбце _hack\_license_ содержатся номера лицензий таксистов (без указания имен).
  
**Записи о поездках и оплате**
  
-   Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.
  
-   Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.
  
-   Последние три столбца можно использовать для различных задач машинного обучения. Столбец _tip\_amount_ содержит непрерывный ряд числовых значений и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip\_class_ содержит несколько **меток классов** и поэтому может использоваться в качестве метки для задач многоклассовой классификации.
  
    В этом пошаговом руководстве демонстрируется только задача двоичной классификации. Вы можете самостоятельно попробовать создать модели для двух других задач машинного обучения: регрессии и многоклассовой классификации.
  
-   Все значения, используемые для столбцов меток, основаны на столбце _tip\_amount_ с применением следующих бизнес-правил.
  
    |Имя производного столбца|Правило|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Создание хранимой процедуры с помощью rxHistogram для построения данных

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!IMPORTANT]
> Начиная с версии SQL Server 2019 механизм изоляции изменился. Поэтому необходимо предоставить соответствующие разрешения для каталога, в котором хранится файл с графиком. Дополнительные сведения о настройке этих разрешений см. в разделе [Разрешения для файлов программы | SQL Server 2019 в Windows: изменения в изоляции в Службах машинного обучения](../install/sql-server-machine-learning-services-2019.md#file-permissions).
::: moniker-end

Чтобы создать диаграмму, используйте [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), одну из улучшенных функций R, доступных в [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). На этом шаге выполняется построение гистограммы на основе данных, полученных из запроса [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эту функцию можно включить в хранимую процедуру **RxPlotHistogram**.

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в обозревателе объектов щелкните правой кнопкой мыши базу данных **NYCTaxi_Sample** и выберите пункт **Создать запрос**.

2. Вставьте следующий скрипт для создания хранимой процедуры, которая строит гистограмму. Этому примеру задано имя **RxPlotHistogram**.

    ```sql
    CREATE PROCEDURE [dbo].[RxPlotHistogram]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =  
      N'SELECT tipped FROM [dbo].[nyctaxi_sample]'  
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

В этом скрипте необходимо обратить внимание на следующие ключевые моменты. 
  
+ Переменная `@query` определяет текст запроса (`'SELECT tipped FROM nyctaxi_sample'`), который передается в скрипт R в качестве аргумента входной переменной `@input_data_1`. Для скриптов R, которые выполняются в виде внешних процессов, требуется сопоставление "один-к-одному" между входными данными скрипта и входными данными системной хранимой процедуры [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), запускающей сеанс R на SQL Server.
  
+ В скрипте R переменная (`image_file`) определяется для хранения изображения. 

+ Затем из библиотеки RevoScaleR вызывается функция **rxHistogram** для создания диаграммы.
  
+ Для устройства R задается значение **off**, так как эта команда выполняется в виде внешнего скрипта в SQL Server. Обычно при использовании высокоуровневой команды построения диаграммы в среде R открывается графическое окно, называемое *устройством*. Если вы записываете данные в файл или обрабатываете результат каким-либо иным способом, устройство можно отключить.
  
+ Графический объект R сериализуется в кадр данных R для вывода.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Выполнение хранимой процедуры и экспорт двоичных данных в файл изображения с помощью служебной программы bcp

Эта хранимая процедура возвращает изображение в виде потока данных varbinary, которые, очевидно, нельзя просмотреть напрямую. Однако вы можете использовать служебную программу **bcp** для получения данных varbinary и сохранения их в виде файла изображения на клиентском компьютере.
  
1. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]выполните следующую инструкцию:
  
    ```sql
    EXEC [dbo].[RxPlotHistogram]
    ```
  
    **Результаты**
    
    *plot* *0xFFD8FFE000104A4649...*
  
2. Откройте окно командной строки PowerShell и выполните следующую команду, указав в качестве аргументов соответствующие имя экземпляра, имя базы данных, имя пользователя и учетные данные. Пользователи, которые используют удостоверения Windows, могут заменить **-U** и **-P** на **-T**.
  
    ```powershell
    bcp "exec RxPlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  NYCTaxi_Sample  -U <user name> -P <password> -T
    ```

    > [!NOTE]
    > В параметрах команды bcp учитывается регистр.
  
3. Если подключение успешно установлено, появится запрос на ввод дополнительных сведений о формате графического файла. 

   Нажимайте клавишу ВВОД, чтобы принять значения по умолчанию, за исключением указанных ниже изменений.
    
   + Для **длины префикса диаграммы поля**введите значение 0.
  
   + Введите **Y** , если необходимо сохранить выходные параметры для повторного использования в будущем.
  
    ```powershell
    Enter the file storage type of field plot [varbinary(max)]: 
    Enter prefix-length of field plot [8]: 0
    Enter length of field plot [0]:
    Enter field terminator [none]:
  
    Do you want to save this format information in a file? [Y/n]
    Host filename [bcp.fmt]:
    ```
  
    **Результаты**
    
    ```powershell
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > Если сохранить сведения о формате в файл (bcp.fmt), программа **bcp** создаст определение формата, которое можно применять к схожим командам в дальнейшем, не получая запросы на задание параметров формата графического файла. Чтобы использовать файл формата, добавьте `-f bcp.fmt` в конец любой командной строки после аргумента пароля.
  
4.  Выходной файл будет создан в том же каталоге, в котором выполнялась команда PowerShell. Чтобы просмотреть диаграмму, просто откройте файл plot.jpg.
  
    ![поездки в такси с чаевыми и без них](media/rsql-devtut-tippedornot.jpg "поездки в такси с чаевыми и без них")  
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Создание хранимой процедуры с помощью Hist и нескольких выходных форматов

Как правило, специалисты по анализу создают несколько визуализаций, чтобы рассмотреть данные с разных сторон. В этом примере вы создадите хранимую процедуру с именем **RPlotHist** для построения гистограмм, точечных и других диаграмм R в форматах JPG и PDF.

Эта хранимая процедура использует функцию **Hist** для создания гистограммы, экспортируя двоичные данных в популярные форматы, такие как JPG, PDF и PNG. 

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в обозревателе объектов щелкните правой кнопкой мыши базу данных **NYCTaxi_Sample** и выберите пункт **Создать запрос**.

2. Вставьте следующий скрипт для создания хранимой процедуры, которая строит гистограмму. Этому примеру задано имя **RPlotHist**.
  
    ```sql
    CREATE PROCEDURE [dbo].[RPlotHist]  
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
  
+ Все файлы сохраняются в локальной папке C:\temp\Plots. Папка назначения определяется аргументами, предоставляемыми скрипту R в рамках хранимой процедуры.  Чтобы поменять папку назначения, измените значение переменной `mainDir`.

+ Чтобы вывести файлы в другую папку, измените значение переменной `mainDir` в скрипте R, встроенном в хранимую процедуру. Скрипт также можно изменить так, чтобы данные выводились в других форматах, в большее количество файлов и т. д.

### <a name="execute-the-stored-procedure"></a>Выполнение хранимой процедуры

Выполните следующую инструкцию, чтобы экспортировать двоичные данные диаграммы в форматы файлов JPEG и PDF.

```sql
EXEC RPlotHist
```

**Результаты**
    
```sql
STDOUT message(s) from external script:
[1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 

C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]

C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
```

Числа в именах файлов создаются случайным образом, чтобы исключить ошибку при попытке записи в существующий файл.

### <a name="view-output"></a>Просмотр выходных данных 

Чтобы просмотреть диаграмму, откройте папку назначения и просмотрите файлы, созданные кодом R в хранимой процедуре.

1. Перейдите в папку, указанную в сообщении STDOUT (в примере это C:\temp\plots\).

2. Откройте `rHistogram_Tipped.jpg`, чтобы отобразить число поездок, за которые были получены чаевые, в сравнении с числом поездок без чаевых. (Эта гистограмма очень похожа на ту, которая была создана в предыдущем шаге.)

3. Откройте `rHistograms_Tip_and_Fare_Amount.pdf`, чтобы просмотреть распределение размеров чаевых в сравнении с суммами по тарифу.
    
  ![гистограмма, показывающая распределение значений в столбцах tip_amount и fare_amount](media/rsql-devtut-tipamtfareamt.PNG "гистограмма, показывающая распределение значений в столбцах tip_amount и fare_amount")

4. Откройте `rXYPlots_Tip_vs_Fare_Amount.pdf`, чтобы просмотреть точечную диаграмму с суммой по тарифу по оси X и размером чаевых по оси Y.

   ![диаграмма с размерами чаевых, наложенная на диаграмму с суммами по тарифу](media/rsql-devtut-tipamtbyfareamt.PNG "диаграмма с размерами чаевых, наложенная на диаграмму с суммами по тарифу")

## <a name="next-lesson"></a>Следующее занятие

[Занятие 2. Создание характеристик данных с помощью T-SQL](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Настройка демонстрационных данных по работе такси в Нью-Йорке](demo-data-nyctaxi-in-sql.md)

---
title: Занятие 1. Просмотр и визуализация данных с помощью R и T-SQL
description: Учебник, показывающий, как исследовать и визуализировать данные SQL Server с помощью функций R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2c204e06edd830d8036b6d0119ce1aff1a9c6833
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "68715373"
---
# <a name="lesson-1-explore-and-visualize-the-data"></a>Занятие 1. Просмотр и визуализация данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья является частью руководства для разработчиков SQL, посвященных использованию R в SQL Server.

На этом шаге вы просматриваете образец данных, а затем создаете несколько графиков с помощью [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) из [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и универсальной функции [хист](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) в Base R. Эти функции R уже включены в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Ключевая цель этого занятия — показать, как вызывать функции R из [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимых процедурах и сохранять результаты в форматах файлов приложения:

+ Создайте хранимую процедуру с помощью **RxHistogram** , чтобы создать график R как данные типа varbinary. Используйте **bcp** для экспорта двоичного потока в файл изображения.
+ Создайте хранимую процедуру с помощью **хист** , чтобы создать график, сохранив результаты в виде JPG-файла и выходных данных в формате PDF.

> [!NOTE]
> Поскольку визуализация — это мощный инструмент для понимания формы данных и распространения, R предоставляет ряд функций и пакетов для создания гистограмм, точечных диаграмм, блочных диаграмм и других графов просмотра данных. Как правило, R создает изображения с помощью устройства R для графических выходных данных, которые можно записать и сохранить в виде типа данных **varbinary** для отрисовки в приложении. Также можно сохранять изображения в любом из форматов файлов поддержки (. JPG,. PDF и т. д.).

## <a name="review-the-data"></a>Проверка данных

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Поэтому сначала уделите минуту, чтобы проверить образец данных, если вы еще этого не сделали.

В исходном общедоступном наборе данных идентификаторы и записи путешествий такси были предоставлены в отдельных файлах. Тем не менее, чтобы упростить использование примеров данных, два исходных набора будут соединены со столбцами _Medallion_, _hack \_license_и _\_datetime отправки_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**
  
-   Столбец _Medallion_ представляет уникальный идентификационный номер такси.
  
-   В столбце " _\_license хакеров_ " содержится номер лицензии драйвера такси (анонимный).
  
**Записи о поездках и оплате**
  
-   Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.
  
-   Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.
  
-   Последние три столбца можно использовать для различных задач машинного обучения. Столбец _tip \_amount_ содержит непрерывные числовые значения и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip \_class_ имеет несколько **меток классов** и поэтому может использоваться в качестве метки для многоклассовых задач классификации.
  
    В этом пошаговом руководстве демонстрируется только задача двоичной классификации. Вы можете самостоятельно попробовать создать модели для двух других задач машинного обучения: регрессии и многоклассовой классификации.
  
-   Значения, используемые для столбцов меток, основаны на столбце _tip \_amount_ , использующем следующие бизнес-правила:
  
    |Имя производного столбца|Правило|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Создание хранимой процедуры с помощью rxHistogram для построения данных

Чтобы создать график, используйте [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), одну из улучшенных функций R, предоставляемых в [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). Этот шаг отображает гистограмму на основе данных из [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Эту функцию можно включить в хранимую процедуру **плотрксхистограм**.

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в обозревателе объектов щелкните правой кнопкой мыши базу данных **NYCTaxi_Sample** и выберите **создать запрос**.

2. Вставьте следующий скрипт, чтобы создать хранимую процедуру, которая отображает гистограмму. Этот пример называется **рплотрксхистограм*.

    ```sql
    CREATE PROCEDURE [dbo].[RxPlotHistogram]
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

Ключевые моменты, на которые следует ознакомиться в этом сценарии, включают следующее: 
  
+ Переменная `@query` определяет текст запроса (`'SELECT tipped FROM nyctaxi_sample'`), который передается в скрипт R в качестве аргумента входной переменной `@input_data_1`. Для скриптов R, выполняемых как внешние процессы, необходимо иметь однозначное соответствие между входными данными для скрипта и входными данными для системной хранимой процедуры [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) , запускающей сеанс R на SQL Server.
  
+ В скрипте R переменная (`image_file`) определяется для хранения изображения. 

+ Функция **rxHistogram** из библиотеки RevoScaleR вызывается для создания графика.
  
+ Устройство R имеет значение **Off** , так как эта команда выполняется как внешний скрипт в SQL Server. Как правило, при выдаче команды на высоком уровне в языке r открывается графическое окно, называемое *устройством*. Устройство можно отключить, если вы записываете данные в файл или обрабатываете результат другим способом.
  
+ Графический объект R сериализуется в кадр данных R для вывода.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Выполнение хранимой процедуры и экспорт двоичных данных в файл изображения с помощью программы bcp

Эта хранимая процедура возвращает изображение в виде потока данных varbinary, которые, очевидно, нельзя просмотреть напрямую. Однако вы можете использовать служебную программу **bcp** для получения данных varbinary и сохранения их в виде файла изображения на клиентском компьютере.
  
1. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]выполните следующую инструкцию:
  
    ```sql
    EXEC [dbo].[RxPlotHistogram]
    ```
  
    **Результаты**
    
    *построить график* *0xFFD8FFE000104A4649...*
  
2. Откройте командную строку PowerShell и выполните следующую команду, указав в качестве аргументов соответствующие имя экземпляра, базу данных, имя пользователя и учетные данные. Для тех, кто использует удостоверения Windows, можно заменить **-U** и **-P** на **-T**.
  
    ```powershell
    bcp "exec RxPlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  NYCTaxi_Sample  -U <user name> -P <password> -T
    ```

    > [!NOTE]
    > При переключении команд для bcp учитывается регистр.
  
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
  
    ![поездки в такси с советами и без них](media/rsql-devtut-tippedornot.jpg "поездки в такси с советами и без них")  
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Создание хранимой процедуры с помощью Хист и нескольких выходных форматов

Как правило, специалисты по обработке и анализу данных создают несколько визуализаций данных, чтобы получить представление о данных с разных перспектив. В этом примере создается хранимая процедура с именем **рплосист** для записи гистограмм, точечных и других графических объектов R в. JPG и. Формат PDF.

Эта хранимая процедура использует функцию **хист** для создания гистограммы, экспорта двоичных данных в популярные форматы, такие как. JPG,. PDF и. Файле. 

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в обозревателе объектов щелкните правой кнопкой мыши базу данных **NYCTaxi_Sample** и выберите **создать запрос**.

2. Вставьте следующий скрипт, чтобы создать хранимую процедуру, которая отображает гистограмму. Этот пример называется **рплосист** .
  
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
  
+ Все файлы сохраняются в локальной папке К:\темп\плотс. Папка назначения определяется аргументами, предоставляемыми скрипту R в рамках хранимой процедуры.  Чтобы поменять папку назначения, измените значение переменной `mainDir`.

+ Чтобы вывести файлы в другую папку, измените значение переменной `mainDir` в скрипте R, встроенном в хранимую процедуру. Скрипт также можно изменить так, чтобы данные выводились в других форматах, в большее количество файлов и т. д.

### <a name="execute-the-stored-procedure"></a>Выполнение хранимой процедуры

Выполните следующую инструкцию, чтобы экспортировать двоичные данные графики в форматы файлов JPEG и PDF.

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

Числа в именах файлов создаются случайным образом, чтобы гарантировать, что при попытке записи в существующий файл не возникает ошибка.

### <a name="view-output"></a>Просмотреть выходные данные 

Чтобы просмотреть график, откройте папку назначения и просмотрите файлы, созданные кодом R в хранимой процедуре.

1. Перейдите в папку, указанную в сообщении STDOUT (в данном примере это К:\темп\плотс \)

2. Откройте `rHistogram_Tipped.jpg`, чтобы отобразить количество поездок, которые получили TIP, и поездки, которые не получили TIP. (Эта гистограмма во многом аналогична той, которая была создана на предыдущем шаге.)

3. Откройте `rHistograms_Tip_and_Fare_Amount.pdf`, чтобы просмотреть распределение сумм TIP, построенных по суммам FARE.
    
  ![Гистограмма, показывающая tip_amount и fare_amount](media/rsql-devtut-tipamtfareamt.PNG "Гистограмма, показывающая tip_amount и fare_amount")

4. Откройте `rXYPlots_Tip_vs_Fare_Amount.pdf`, чтобы просмотреть точечная диаграмма с суммой FARE на оси x и суммой TIP по оси y.

   ![сумма TIP, построенная поверх суммы FARE](media/rsql-devtut-tipamtbyfareamt.PNG "сумма TIP, построенная поверх суммы FARE")

## <a name="next-lesson"></a>Следующее занятие

[Занятие 2. Создание функций данных с помощью T-SQL](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Настройка демонстрационных данных такси Нью](demo-data-nyctaxi-in-sql.md)

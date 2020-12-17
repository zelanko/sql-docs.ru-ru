---
title: Учебник по R. Изучение и визуализация данных
titleSuffix: SQL machine learning
description: Изучите образцы данных и создайте несколько графиков, чтобы подготовиться к использованию двоичной классификации в R с помощью машинного обучения SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/15/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||>=azuresqldb-mi-current'
ms.openlocfilehash: 571b49dfa3ce555aad02ffe8d6ba7c68a033bbdc
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470125"
---
# <a name="r-tutorial-explore-and-visualize-data"></a>Учебник по R. Изучение и визуализация данных
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

Во второй части этой серии руководств вы изучите образец данных и создадите несколько графиков. Далее вы узнаете, как сериализовать графические объекты на Python, а затем десериализовать эти объекты и создать графики.

Во второй части этой серии руководств вы изучите образец данных, а затем создаете несколько графиков с помощью универсальных функций `barplot` и `hist` в базовом R.

Цель этой статьи — показать, как вызывать функции R из [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимые процедуры и сохранять результаты в форматах файлов приложения.

+ Создание хранимой процедуры с помощью `barplot` для построения диаграммы R в виде данных типа varbinary. Использование **bcp** для экспорта двоичного потока в файл изображения.
+ Создание хранимой процедуры с помощью `hist` для построения диаграммы и сохранения результатов в формате JPG и PDF.

> [!NOTE]
> Поскольку визуализация является мощным инструментом для понимания формы и распространения данных, R предоставляет ряд функций и пакетов для создания гистограмм, точечных диаграмм, блочных диаграмм и других типов диаграмм для исследования данных. Как правило, изображения в R создаются с помощью устройства R для вывода графики. Выходные данные можно записать и сохранить с типом данных **varbinary** для отрисовки в приложении. Изображения можно также сохранять в любом из поддерживаемых форматов файлов (JPG, PDF и т. д.).

Работая с этой статьей, вы узнаете о следующем.

> [!div class="checklist"]
> + Изучение образца данных
> + Создание графиков с помощью языка R в T-SQL
> + Выходные графики в нескольких форматах файлов

В [первой части](r-taxi-classification-introduction.md) были установлены необходимые компоненты и восстановлена демонстрационная база данных.

В [третьей части](r-taxi-classification-create-features.md) вы узнаете, как создавать функции из необработанных данных с помощью функции Transact-SQL. Затем вы вызовите эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.

В [четвертой части](r-taxi-classification-train-model.md) вы научитесь загружать модули и вызывать необходимые функции для создания и обучения модели с помощью хранимой процедуры SQL Server.

Из [пятой части](r-taxi-classification-deploy-model.md) вы узнаете, как ввести в эксплуатацию модели, которые были обучены и сохранены в соответствии с инструкциями в четвертой части.

## <a name="review-the-data"></a>Изучение данных

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Для начала немного изучите образец данных, если вы это еще не сделали.

В исходном общедоступном наборе данных идентификаторы такси и записи о поездках были предоставлены в отдельных файлах. Однако, чтобы образец данных было удобнее использовать, два исходных набора данных были объединены по столбцам _medallion_, _hack\_license_, и _pickup\_datetime_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**
  
+ В столбце _medallion_ представлены уникальные идентификационные номера такси.
  
+ В столбце _hack\_license_ содержатся номера лицензий таксистов (без указания имен).
  
**Записи о поездках и оплате**
  
+ Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.
  
+ Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.
  
+ Последние три столбца можно использовать для различных задач машинного обучения. Столбец _tip\_amount_ содержит непрерывный ряд числовых значений и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip\_class_ содержит несколько **меток классов** и поэтому может использоваться в качестве метки для задач многоклассовой классификации.
  
  В этом пошаговом руководстве демонстрируется только задача двоичной классификации. Вы можете самостоятельно попробовать создать модели для двух других задач машинного обучения: регрессии и многоклассовой классификации.
  
+ Все значения, используемые для столбцов меток, основаны на столбце _tip\_amount_ с применением следующих бизнес-правил.
  
  |Имя производного столбца|Правило|
  |-|-|
  |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
  |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-plots-using-r-in-t-sql"></a>Создание графиков с помощью языка R в T-SQL

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15"
> [!IMPORTANT]
> Начиная с SQL Server 2019, механизм изоляции требует предоставления соответствующих разрешений каталогу, в котором хранится файл графика. Дополнительные сведения о настройке этих разрешений см. в разделе [Разрешения для файлов программы | SQL Server 2019 в Windows: изменения в изоляции в Службах машинного обучения](../install/sql-server-machine-learning-services-2019.md#file-permissions).
::: moniker-end

Чтобы создать график, используйте функцию R `barplot`. На этом шаге выполняется построение гистограммы на основе данных, полученных из запроса [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эту функцию можно включить в хранимую процедуру **RPlotHistogram**.

1. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в обозревателе объектов щелкните правой кнопкой мыши базу данных **NYCTaxi_Sample** и выберите пункт **Создать запрос**. Также можно выбрать **Создать записную книжку** в меню **Файл** Azure Data Studio и подключиться к базе данных.

2. Вставьте следующий скрипт для создания хранимой процедуры, которая строит гистограмму. Этому примеру задано имя **RPlotHistogram**.

   ```sql
   CREATE PROCEDURE [dbo].[RPlotHistogram]
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
      barplot(table(InputDataSet$tipped), main = "Tip Histogram", col="lightgreen", xlab="Tipped or not", ylab = "Counts", space=0)
      dev.off();  
      OutputDataSet <- data.frame(data=readBin(file(image_file, "rb"), what=raw(), n=1e6));  
      ',  
      @input_data_1 = @query  
      WITH RESULT SETS ((plot varbinary(max)));  
   END
   GO
   ```

В этом скрипте необходимо обратить внимание на следующие ключевые моменты.
  
+ Переменная `@query` определяет текст запроса (`'SELECT tipped FROM nyctaxi_sample'`), который передается в скрипт R в качестве аргумента входной переменной `@input_data_1`. Для скриптов R, которые выполняются в виде внешних процессов, требуется сопоставление "один-к-одному" между входными данными скрипта и входными данными системной хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), запускающей сеанс R на SQL Server.
  
+ В скрипте R переменная (`image_file`) определяется для хранения изображения.

+ Функция `barplot` вызывается для создания графика.
  
+ Для устройства R задается значение **off**, так как эта команда выполняется в виде внешнего скрипта в SQL Server. Обычно при использовании высокоуровневой команды построения диаграммы в среде R открывается графическое окно, называемое *устройством*. Если вы записываете данные в файл или обрабатываете результат каким-либо иным способом, устройство можно отключить.
  
+ Графический объект R сериализуется в кадр данных R для вывода.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Выполнение хранимой процедуры и экспорт двоичных данных в файл изображения с помощью служебной программы bcp

Эта хранимая процедура возвращает изображение в виде потока данных varbinary, которые, очевидно, нельзя просмотреть напрямую. Однако вы можете использовать служебную программу **bcp** для получения данных varbinary и сохранения их в виде файла изображения на клиентском компьютере.
  
1. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]выполните следующую инструкцию:
  
    ```sql
    EXEC [dbo].[RPlotHistogram]
    ```
  
    **Результаты**
    
    *plot* *0xFFD8FFE000104A4649...*
  
2. Откройте окно командной строки PowerShell и выполните следующую команду, указав в качестве аргументов соответствующие имя экземпляра, имя базы данных, имя пользователя и учетные данные. Пользователи, которые используют удостоверения Windows, могут заменить **-U** и **-P** на **-T**.
  
   ```powershell
   bcp "exec RPlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  NYCTaxi_Sample  -U <user name> -P <password> -T
   ```

   > [!NOTE]
   > В параметрах команды bcp учитывается регистр.
  
3. Если подключение успешно установлено, появится запрос на ввод дополнительных сведений о формате графического файла.

   Нажимайте клавишу ВВОД, чтобы принять значения по умолчанию, за исключением указанных ниже изменений.

   + Для **длины префикса графика поля** введите значение 0.
  
   + Введите **Y** , если необходимо сохранить выходные параметры для повторного использования в будущем.
  
   ```text
   Enter the file storage type of field plot [varbinary(max)]: 
   Enter prefix-length of field plot [8]: 0
   Enter length of field plot [0]:
   Enter field terminator [none]:
  
   Do you want to save this format information in a file? [Y/n]
   Host filename [bcp.fmt]:
   ```
  
   **Результаты**

   ```text
   Starting copy...
   1 rows copied.
   Network packet size (bytes): 4096
   Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
   ```

   > [!TIP]
   > Если сохранить сведения о формате в файл (bcp.fmt), программа **bcp** создаст определение формата, которое можно применять к схожим командам в дальнейшем, не получая запросы на задание параметров формата графического файла. Чтобы использовать файл формата, добавьте `-f bcp.fmt` в конец любой командной строки после аргумента пароля.
  
4. Выходной файл будет создан в том же каталоге, в котором выполнялась команда PowerShell. Чтобы просмотреть диаграмму, просто откройте файл plot.jpg.
  
   ![поездки в такси с чаевыми и без них](media/rsql-devtut-tippedornot.jpg "поездки в такси с чаевыми и без них")  
  
## <a name="create-a-stored-procedure-using-hist"></a>Создание хранимой процедуры с помощью `hist`

Как правило, специалисты по анализу создают несколько визуализаций, чтобы рассмотреть данные с разных сторон. В этом примере вы создадите хранимую процедуру с именем **RPlotHist** для построения гистограмм, точечных и других диаграмм R в форматах JPG и PDF.

Эта хранимая процедура использует функцию `hist` для создания гистограммы, экспортируя двоичные данных в популярные форматы, такие как JPG, PDF и PNG.

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
  
В этом скрипте необходимо обратить внимание на следующие ключевые моменты.

+ Выходные данные запроса SELECT в хранимой процедуре сохраняются в кадре данных R по умолчанию ( `InputDataSet`). После этого можно вызывать различные функции построения диаграмм R для создания графических файлов. Встроенный скрипт R по большей части представляет собой параметры для этих графических функций, таких как `plot` и `hist`.
  
+ Для устройства R задается значение **off**, так как эта команда выполняется в виде внешнего скрипта в SQL Server. Обычно при использовании высокоуровневой команды построения диаграммы в среде R открывается графическое окно, называемое *устройством*. Если вы записываете данные в файл или обрабатываете результат каким-либо иным способом, устройство можно отключить.
  
+ Все файлы сохраняются в локальной папке C:\temp\Plots. Папка назначения определяется аргументами, предоставляемыми скрипту R в рамках хранимой процедуры. Чтобы вывести файлы в другую папку, измените значение переменной `mainDir` в скрипте R, встроенном в хранимую процедуру. Скрипт также можно изменить так, чтобы данные выводились в других форматах, в большее количество файлов и т. д.

### <a name="execute-the-stored-procedure"></a>Выполнение хранимой процедуры

Выполните следующую инструкцию, чтобы экспортировать двоичные данные диаграммы в форматы файлов JPEG и PDF.

```sql
EXEC RPlotHist
```

**Результаты**

```text
STDOUT message(s) from external script:
[1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 

C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]

C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
```

Числа в именах файлов создаются случайным образом, чтобы исключить ошибку при попытке записи в существующий файл.

### <a name="view-output"></a>Просмотр выходных данных

Чтобы просмотреть диаграмму, откройте папку назначения и просмотрите файлы, созданные кодом R в хранимой процедуре.

1. Перейдите в папку, указанную в сообщении STDOUT (в примере это C:\temp\plots\).

2. Откройте `rHistogram_Tipped.jpg`, чтобы отобразить количество поездок с чаевыми и без них (эта гистограмма похожа на ту, которая была создана на предыдущем шаге).

3. Откройте `rHistograms_Tip_and_Fare_Amount.pdf`, чтобы просмотреть распределение размеров чаевых в сравнении с суммами по тарифу.

   ![гистограмма, показывающая распределение значений в столбцах tip_amount и fare_amount](media/rsql-devtut-tipamtfareamt.PNG "гистограмма, показывающая распределение значений в столбцах tip_amount и fare_amount")

4. Откройте `rXYPlots_Tip_vs_Fare_Amount.pdf`, чтобы просмотреть точечную диаграмму с суммой по тарифу по оси X и размером чаевых по оси Y.

   ![диаграмма с размерами чаевых, наложенная на диаграмму с суммами по тарифу](media/rsql-devtut-tipamtbyfareamt.PNG "диаграмма с размерами чаевых, наложенная на диаграмму с суммами по тарифу")

## <a name="next-steps"></a>Дальнейшие шаги

Работая с этой статьей, вы выполните следующие задачи:

> [!div class="checklist"]
> + Изучен образец данных
> + Создание графиков с помощью языка R в T-SQL
> + Выходные графики в нескольких форматах файлов

> [!div class="nextstepaction"]
> [Учебник по R. Создание характеристик данных](r-taxi-classification-create-features.md)
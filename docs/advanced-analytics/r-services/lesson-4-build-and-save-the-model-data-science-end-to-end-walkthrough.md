---
title: "Занятие&#160;4. Создание и сохранение модели (пошаговое руководство по обработке и анализу данных) | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
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
ms.assetid: 69b374c1-2042-4861-8f8b-204a6297c0db
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Занятие&#160;4. Создание и сохранение модели (пошаговое руководство по обработке и анализу данных)
На этом занятии вы узнаете, как создать модель машинного обучения и сохранить ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="creating-a-classification-model"></a>Создание модели классификации  
Модель, которую вы создадите, представляет собой двоичный классификатор, который прогнозирует, получит ли таксист чаевые за определенную поездку. Вы используете источник данных, созданный на предыдущем занятии ( `featureDataSource,` ), для обучения классификатора с помощью логистической регрессии.  
  
В модели будут использоваться следующие характеристики:  
  
-   passenger_count  
  
-   trip_distance  
  
-   trip_time_in_secs  
  
-   direct_distance  

### <a name="create-the-model-using-rxlogit"></a>Создание модели с помощью rxLogit  
1.  Вызовите функцию *rxLogit*, входящую в пакет **RevoScaleR**, чтобы создать модель логистической регрессии.  
  
    ```R  
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource))    
    ```  
  
2.  После создания модели ее необходимо будет проверить с помощью функции `summary` и просмотреть коэффициенты.  
  
    ```  
    summary(logitObj)  
    ```  

     *Результаты*

     *Результаты логистической регрессии для: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*  
     *direct_distance*  
     *Данные: featureDataSource (RxSqlServerData Data Source)*  
     *Зависимые переменные: tipped*  
     *Всего независимых переменных: 5*   
     *Число допустимых наблюдений: 17 068*  
     *Число отсутствующих наблюдений: 0*   
     *-2\*LogLikelihood: 23540,0602 (остаточное отклонение при 17063 степеней свободы)*  
     *Коэффициенты:*  
     *Значение z оценки средней квадратической ошибки Pr(>|z|)*   
     *(Отрезок)       -2,509e-03  3,223e-02  -0,078  0,93793*   
     *passenger_count   -5,753e-02  1,088e-02  -5,289 1,23e-07\*\*\**  
     *trip_distance     -3,896e-02  1,466e-02  -2,658  0,00786\*\**   
     *trip_time_in_secs  2,115e-04  4,336e-05   4.878 1,07e-06\*\*\**  
     *direct_distance    6,156e-02  2,076e-02   2,966  0,00302\*\**   
     *---*  
     *Коды значимости:  0 "\*\*\*" 0,001 "\*\*" 0,01 "\*" 0,05 "." 0.1 ‘ ’ 1*  
     *Коэффициент переноса итоговой матрицы дисперсий и ковариаций: 48,3933*   
     *Число итераций: 4*  
  
### <a name="use-the-logistic-regression-model-for-scoring"></a>Использование модели логистической регрессии для оценки  
Теперь, когда модель создана, ее можно использовать для прогнозирования того, получит ли таксист чаевые за определенную поездку.  
  
1.  Сначала определите объект данных, который будет использоваться для хранения результатов оценки.  
  
    ```R  
    scoredOutput <- RxSqlServerData(  
      connectionString = connStr,  
      table = "taxiScoreOutput"  )  
    ```  
    + Чтобы упростить этот пример, в качестве входных данных мы используем для модели логистической регрессии тот же источник данных `featureDataSource` , который использовался для обучения модели.  Чаще всего для оценки применяются новые данные либо для тестирования и обучения используются разные данные.  
  
    + Результаты прогнозирования сохраняются в таблице _taxiscoreOutput_. Обратите внимание на то, что при создании таблицы с помощью функции `rxSqlServerData`схема для нее не определяется, а получается из выходного объекта *scoredOutput* функции `rxPredict`.  
  
    + Для создания таблицы, в которой будут храниться прогнозируемые значения, у имени входа SQL, с помощью которого выполняется функция данных `rxSqlServer` , должны быть права DDL в базе данных. Если имя входа не имеет права на создание таблиц, выполнение инструкции завершится сбоем.  
  
2.  Вызовите функцию *rxPredict*, чтобы создать результаты.  
  
    ```R  
    rxPredict(modelObject = logitObj, data = featureDataSource, outData = scoredOutput,   
                       predVarNames = "Score", type = "response",   
                       writeModelVars = TRUE, overwrite = TRUE)  
    ```  

  
## <a name="plotting-model-accuracy"></a>Построение диаграммы точности модели  
Чтобы получить представление о точности модели, можно воспользоваться функцией *rxRocCurve* для построения диаграммы зависимости чувствительности от частоты ложно положительных заключений. Так как *rxRocCurve* — это одна из новых функций, входящих в состав пакета RevoScaleR и поддерживающих удаленные контексты вычислений, у вас есть два варианта.  
  
+ Вы можете использовать функцию `rxRocCurve` для построения графика в удаленном контексте вычисления с последующим возвращением графика в локальный клиент.
+ Также можно импортировать данные на клиентский компьютер R и использовать другие функции построения диаграмм R для создания графика производительности.  
  
В этом разделе используются оба приема.  
  
### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Построение диаграммы в удаленном контексте вычислений (SQL Server)  
  
1.  Вызовите функцию *rxRocCurve*, предоставив данные, определенные ранее в качестве входных.  
  
    ```R  
    rxRocCurve( "tipped", "Score", scoredOutput)  
    ```  
  
    Обратите внимание на то, что также необходимо указать метку столбца tipped (переменную, которую вы пытаетесь спрогнозировать) и имя столбца, в котором сохраняется прогноз (_Score_).  
  
2.  Просмотрите график, открыв графическое устройство R или щелкнув окно **Plot** в RStudio.  
  
    ![ROC plot for the model](../../advanced-analytics/r-services/media/rsql-e2e-rocplot.png "ROC plot for the model")  

    График строится в удаленном контексте вычислений, а затем возвращается в вашу среду R.   
    
### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Создание диаграмм в локальном контексте вычислений с помощью данных из SQL Server  
  
1.  Используйте функцию *rxImport* для переноса указанных данных в локальную среду R.  
  
    ```R  
    scoredOutput = rxImport(scoredOutput)  
    ```  
  
2.  Загрузив данные в локальную память, можно вызвать библиотеку **ROCR**, чтобы сформировать прогнозы и создать диаграмму.  
  
    ```R  
    library('ROCR')  
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped)  
  
    acc.perf = performance(pred, measure = 'acc')  
    plot(acc.perf)  
    ind = which.max( slot(acc.perf, 'y.values')[[1]] )  
    acc = slot(acc.perf, 'y.values')[[1]][ind]  
    cutoff = slot(acc.perf, 'x.values')[[1]][ind]  
    ```  
  
3.  Приведенный ниже график создается в обоих случаях.  
  
    ![plotting model performance using R](../../advanced-analytics/r-services/media/rsql-e2e-performanceplot.png "plotting model performance using R")  
  
## <a name="deploying-a-model"></a>Развертывание модели  

Если после создания модели вы решите, что она работает хорошо, ее можно *ввести в эксплуатацию*. Так как службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] позволяют вызывать модель R с помощью хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] , использовать язык R в клиентском приложении крайне просто.  
  
Однако перед вызовом модели из внешнего приложения необходимо сохранить ее в базе данных, используемой в рабочей среде. В службах [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]модели обучения хранятся в двоичной форме в одном столбце типа **varbinary(max)**.

Таким образом, для перемещения модели обучения из среды R в SQL Server необходимо выполнить следующие действия:  
  
+ сериализовать модель в шестнадцатеричную строку;
+ передать сериализованный объект в базу данных;
+ сохранить модель в столбце varbinary(max).  
  
В этом разделе вы узнаете, как сохранить модель в базе данных и вызвать ее для составления прогнозов.  
  
### <a name="serialize-the-model"></a>Сериализация модели  
  
+  В локальной среде R сериализуйте модель и сохраните ее в переменной.  
  
    ```R  
    modelbin <- serialize(logitObj, NULL)  
    modelbinstr=paste(modelbin, collapse="")  
    ```  
  
    Функция *serialize* входит в состав **базового** пакета R и предоставляет простой низкоуровневый интерфейс для сериализации в подключения. Дополнительные сведения см. на странице [http://www.inside-r.org/r-doc/base/serialize](http://www.inside-r.org/r-doc/base/serialize).  
  
### <a name="move-the-model-to-sql-server"></a>Перемещение модели в SQL Server

+ Откройте подключение ODBC и вызовите хранимую процедуру, чтобы сохранить двоичное представление модели в столбце базы данных. 
  
    ```R  
    library(RODBC)  
    conn <- odbcDriverConnect(connStr )  
  
    # persist model by calling a stored procedure from SQL  
    q<-paste("EXEC PersistModel @m='", modelbinstr,"'", sep="")  
    sqlQuery (conn, q)    
    ```  

Для сохранения модели в таблице требуется только инструкция INSERT. Однако для простоты мы использовали хранимую процедуру _PersistModel_. 
 
Для справки ниже приводится полный код хранимой процедуры.  
  
```tsql  
CREATE PROCEDURE [dbo].[PersistModel]  @m nvarchar(max)  
AS  
BEGIN  
        -- SET NOCOUNT ON added to prevent extra result sets from  
        -- interfering with SELECT statements.  
        SET NOCOUNT ON;  
        insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))  
END   
```  
> [!TIP] Мы рекомендуем создавать вспомогательные функции наподобие этой хранимой процедуры, чтобы упростить управление моделями R и их обновление в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
### <a name="invoke-the-saved-model"></a>Вызов сохраненной модели  
После сохранения модели в базе данных ее можно вызвать непосредственно из кода [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью системной хранимой процедуры [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
Например, чтобы сформировать прогнозы, нужно просто подключиться к базе данных и выполнить хранимую процедуру, используя в качестве входных данных сохраненную модель, а также ряд других данных.  
  
Однако если модель используется часто, проще включить входной запрос и вызов модели, а также прочие параметры в пользовательскую хранимую процедуру.  
  
На следующем занятии вы узнаете, как выполнять оценку на основе сохраненной модели с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 5. Развертывание и использование модели (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-5-deploy-and-use-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Предыдущее занятие  
[Занятие 3. Создание характеристик данных (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)  
  
  
  

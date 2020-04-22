---
title: Выполнение заданий Spark. Набор средств Azure для IntelliJ
titleSuffix: SQL Server Big Data Clusters
description: Отправка заданий Spark в кластерах больших данных SQL Server в Azure Toolkit for IntelliJ.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.topic: conceptual
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 604292d548d9368439b810fa4dfebf2d4388929e
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634950"
---
# <a name="submit-spark-jobs-on-big-data-clusters-2019-in-intellij"></a>Отправка заданий Spark в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в IntelliJ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Одним из основных сценариев для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] является возможность отправки заданий Spark. Функция отправки заданий Spark позволяет отправлять локальные файлы JAR или PY со ссылками на [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]. Она также позволяет выполнять файлы JAR или PY, которые уже находятся в файловой системе HDFS. 

## <a name="prerequisites"></a>Предварительные требования

- Кластер больших данных SQL Server.
- Пакет SDK для Java Oracle. Его можно установить с [веб-сайта Oracle](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).
- Среда IntelliJ IDEA. Ее можно установить с [веб-сайта JetBrains](https://www.jetbrains.com/idea/download/).
- Расширение Azure Toolkit for IntelliJ. Инструкции по установке см. в статье [Установка Azure Toolkit for IntelliJ](https://docs.microsoft.com/azure/azure-toolkit-for-intellij-installation).

## <a name="link-sql-server-big-data-cluster"></a>Связывание с кластером больших данных SQL Server
1. Откройте средство IntelliJ IDEA.

2. Если применяется самозаверяющий сертификат, отключите проверку TLS/SSL-сертификата. Для этого в меню **Сервис** последовательно выберите пункты **Azure**, **Проверять SSL-сертификат кластера Spark** и **Отключить**.

    ![Связывание с кластером больших данных SQL Server — отключение TLS/SSL](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-disableSSL.png)

3. Откройте обозреватель Azure, выбрав в меню **View** (Вид) пункт **Tool Windows** (Окна инструментов), а затем — **Azure Explorer** (Обозреватель Azure).
4. Щелкните правой кнопкой мыши узел **SQL Server big data cluster** (Кластер больших данных SQL Server) и выберите пункт **Link SQL Server big data cluster** (Связать с кластером больших данных SQL Server). Введите **сервер**, **имя пользователя** и **пароль**, а затем нажмите кнопку **ОК**.

    ![связывание с кластером больших данных — диалоговое окно](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-dialog.png)

5. Когда появится диалоговое окно с сообщением о ненадежном сертификате сервера, нажмите **Accept** (Принимаю). Настроить сертификат можно позднее. См. раздел, посвященный [сертификатам серверов](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html).

6. Связанный кластер указывается в узле **SQL Server big data cluster** (Кластер больших данных SQL Server). Вы можете отслеживать задание Spark, открыв пользовательский интерфейс журнала Spark и пользовательский интерфейс Yarn. Можно также разорвать связь, щелкнув кластер правой кнопкой мыши.

    ![связывание с кластером больших данных — контекстное меню](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-contextmenu.png)

## <a name="create-a-spark-scala-application-from-spark-template"></a>Создание приложения Spark Scala на основе шаблона Spark

1. Запустите IntelliJ IDEA и создайте проект. В диалоговом окне **New Project** (Новый проект) выполните указанные ниже действия. 

   а. Выберите **Azure Spark/HDInsight** > **Spark Project with Samples (Scala)** (Проект Spark с образцами (Scala)).

   b. В списке **Build tool** (Средство сборки) выберите одно из следующих средств:

      * **Maven** для поддержки мастера создания проектов Scala;
      * **SBT** для управления зависимостями и сборки проекта Scala.

    ![Диалоговое окно New Project (Новый проект)](./media/spark-submit-job-intellij-tool-plugin/create-hdi-scala-app.png)

2. Выберите **Далее**.

3. Мастер создания проектов Scala автоматически определяет, установлен ли подключаемый модуль Scala. Выберите пункт **Установить**.

   ![Проверка подключаемого модуля Scala](./media/spark-submit-job-intellij-tool-plugin/Scala-Plugin-check-Reminder.PNG) 

4. Чтобы скачать подключаемый модуль Scala, нажмите кнопку **ОК**. Следуйте инструкциям, чтобы перезапустить IntelliJ. 

   ![Диалоговое окно установки подключаемого модуля Scala](./media/spark-submit-job-intellij-tool-plugin/Choose-Scala-Plugin.PNG)

5. В окне **New Project** (Новый проект) выполните указанные ниже действия.  

    ![Выбор пакета SDK для Spark](./media/spark-submit-job-intellij-tool-plugin/hdi-new-project.png)

   а. Введите имя и расположение проекта.

   b. В раскрывающемся списке **Project SDK** (Пакет SDK проекта) выберите **Java 1.8** для кластера Spark 2.x или **Java 1.7** для кластера Spark 1.x.

   c. В раскрывающемся списке **Spark version** (Версия Spark) мастер создания проектов Scala включает подходящую версию пакетов SDK для Spark и Scala. Если используется версия кластера Spark более ранняя, чем 2.0, выберите **Spark 1.x**. В противном случае выберите **Spark 2.x**. В этом примере используется **Spark 2.0.2 (Scala 2.11.8)** .

6. Нажмите кнопку **Готово**.

7. Проект Spark автоматически создает артефакт. Чтобы просмотреть артефакт, выполните указанные ниже действия.

   а. В меню **File** (Файл) выберите пункт **Project Structure** (Структура проекта).

   b. В диалоговом окне **Project Structure** (Структура проекта) выберите **Artifacts** (Артефакты), чтобы просмотреть созданный артефакт по умолчанию. Можно также создать собственный артефакт, нажав на знак "плюс" ( **+** ).

      ![Сведения об артефакте в диалоговом окне](./media/spark-submit-job-intellij-tool-plugin/default-artifact.png)
      

## <a name="submit-application-to-sql-server-big-data-cluster"></a>Отправка приложения в кластер больших данных SQL Server
После связывания с кластером больших данных SQL Server в него можно отправить приложение.

1. Настройте конфигурацию в окне **Run/Debug Configurations** (Конфигурации запуска и отладки), щелкните **Apache Spark on SQL Server** (Apache Spark в SQL Server), выберите вкладку **Remotely Run in Cluster** (Удаленный запуск в кластере), задайте параметры, как показано ниже, и нажмите кнопку "ОК".

    ![Добавление конфигурации в интерактивной консоли](./media/spark-submit-job-intellij-tool-plugin/interactive-console-add-config-entry.png)

    ![связывание с кластером больших данных — конфигурация](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-config.png)

    * В поле **Spark clusters (Linux only)** (Кластеры Spark (только Linux)) выберите кластер, в котором должно выполняться приложение.

    * Выберите артефакт из проекта IntelliJ или на жестком диске.

    * Поле **Main class name** (Имя главного класса): значение по умолчанию — имя главного класса из выбранного файла. Класс можно изменить, нажав кнопку с многоточием ( **...** ) и выбрав другой класс.   

    * Поле **Job Configurations** (Конфигурации задания):  значения по умолчанию показаны ниже. Вы можете изменить значение или добавить новые ключ и значение для отправки задания. Дополнительные сведения [REST API Apache Livy](http://livy.incubator.apache.org./docs/latest/rest-api.html)

      ![Значение конфигурации задания в диалоговом окне отправки Spark](./media/spark-submit-job-intellij-tool-plugin/submit-job-configurations.png)

    * Поле **Command line arguments** (Аргументы командной строки): при необходимости можно ввести значения аргументов для главного класса через пробел.

    * Поля **Referenced Jars** (Используемые JAR) и **Referenced Files** (Используемые файлы): можно ввести пути к используемым JAR и файлам, если они есть. Дополнительные сведения [Конфигурация Apache Spark](https://spark.apache.org/docs/latest/configuration.html#runtime-environment) 

      ![Значение файлов JAR в диалоговом окне отправки Spark](./media/spark-submit-job-intellij-tool-plugin/jar-files-meaning.png)

       > [!NOTE]  
       > Инструкции по отправке используемых JAR и файлов см. в следующем разделе: [Отправка ресурсов в кластер](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-storage-explorer)
                         
    * **Upload Path** (Путь отправки): можно указать место хранения для отправляемых ресурсов проекта JAR или Scala. Поддерживаются несколько типов хранилищ: **Use Spark interactive session to upload** (Использовать для отправки интерактивный сеанс Spark) и **Use WebHDFS to upload** (Использовать для отправки WebHDFS).
    
2. Щелкните **SparkJobRun**, чтобы отправить проект в выбранный кластер. На вкладке **Remote Spark Job in Cluster** (Удаленное задание Spark в кластере) внизу показан ход выполнения задания. Чтобы остановить работу приложения, нажмите красную кнопку.  

    ![связывание с кластером больших данных — запуск](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-run.png)

## <a name="spark-console"></a>Консоль Spark
Вы можете запустить локальную консоль Spark (Scala) или консоль интерактивного сеанса Spark Livy (Scala).

### <a name="spark-local-consolescala"></a>Локальная консоль Spark (Scala)
Убедитесь в том, что имеется необходимый файл WINUTILS.EXE.

1. В строке меню выберите **Run (Запуск)**  > **Edit Configurations...** (Изменить конфигурации).

2. В окне **Run/Debug Configurations** (Конфигурации запуска и отладки) в области слева перейдите в раздел **Apache Spark on SQL Server big data cluster (Apache Spark в кластере больших данных SQL Server)**  >  **[Spark on SQL] myApp** ([Spark в SQL] myApp).

3. В главном окне выберите вкладку **Locally Run** (Локальный запуск).

4. Укажите следующие значения и нажмите кнопку **ОК**:

    |Свойство |Значение |
    |----|----|
    |Главный класс задания|значение по умолчанию — имя главного класса из выбранного файла. Класс можно изменить, нажав кнопку с многоточием ( **...** ) и выбрав другой класс.|
    |Переменные среды|Проверьте правильность значения HADOOP_HOME.|
    |Расположение файла WINUTILS.exe|Проверьте правильность пути.|

    ![Настройка конфигурации в локальной консоли](./media/spark-submit-job-intellij-tool-plugin/console-set-configuration.png)

5. В проекте перейдите в **myApp** > **src** > **main** > **scala** > **myApp**.  

6. В строке меню выберите **Tools (Сервис)**  > **Spark Console (Консоль Spark)**  > **Run Spark Local Console(Scala)** (Запустить локальную консоль Spark (Scala)).

7. После этого могут появиться два диалоговых окна с запросом на автоматическое исправление зависимостей. Если нужно исправить их, выберите **Auto Fix** (Автоматическое исправление).

    ![Автоматическое исправление Spark 1](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix1.png)

    ![Автоматическое исправление Spark 2](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix2.png)

8. Консоль должна выглядеть примерно так, как показано ниже. В окне консоли введите `sc.appName` и нажмите клавиши CTRL+ВВОД.  Отобразится результат. Чтобы закрыть локальную консоль, нажмите красную кнопку.

    ![Результат в локальной консоли](./media/spark-submit-job-intellij-tool-plugin/local-console-result.png)


### <a name="spark-livy-interactive-session-consolescala"></a>Консоль интерактивного сеанса Spark Livy (Scala)
Консоль интерактивного сеанса Spark Livy (Scala) поддерживается только в IntelliJ 2018.2 и 2018.3.

1. В строке меню выберите **Run (Запуск)**  > **Edit Configurations...** (Изменить конфигурации).

2. В окне **Run/Debug Configurations** (Конфигурации запуска и отладки) в области слева перейдите в раздел **Apache Spark on SQL Server big data cluster (Apache Spark в кластере больших данных SQL Server)**  >  **[Spark on SQL] myApp** ([Spark в SQL] myApp).

3. В главном окне выберите вкладку **Remotely Run in Cluster** (Удаленный запуск в кластере).

4. Укажите следующие значения и нажмите кнопку **ОК**:

    |Свойство |Значение |
    |----|----|
    |Кластеры Spark (только Linux)|Выберите кластер больших данных SQL Server, в котором должно выполняться приложение.|
    |Имя главного класса|значение по умолчанию — имя главного класса из выбранного файла. Класс можно изменить, нажав кнопку с многоточием ( **...** ) и выбрав другой класс.|

    ![Настройка конфигурации в интерактивной консоли](./media/spark-submit-job-intellij-tool-plugin/interactive-console-configuration.png)

5. В проекте перейдите в **myApp** > **src** > **main** > **scala** > **myApp**.  

6. В строке меню выберите **Tools (Сервис)**  > **Spark Console (Консоль Spark)**  > **Run Spark Livy Interactive Session Console(Scala)** (Запустить консоль интерактивного сеанса Spark Livy (Scala)).

7. Консоль должна выглядеть примерно так, как показано ниже. В окне консоли введите `sc.appName` и нажмите клавиши CTRL+ВВОД.  Отобразится результат. Чтобы закрыть локальную консоль, нажмите красную кнопку.

    ![Результат в интерактивной консоли](./media/spark-submit-job-intellij-tool-plugin/interactive-console-result.png)

### <a name="send-selection-to-spark-console"></a>Отправка выбранного фрагмента в консоль Spark

Для удобства вы можете увидеть результат выполнения скрипта, отправив код в локальную консоль или консоль интерактивного сеанса Livy (Scala). Выделите код в файле Scala, а затем в контекстном меню выберите пункт **Send Selection To Spark Console** (Отправить выделенный фрагмент в консоль Spark). Выделенный код будет отправлен в консоль и выполнен. Результат отобразится в консоли после кода. Консоль проверит наличие ошибок.  

   ![Отправка выбранного фрагмента в консоль Spark](./media/spark-submit-job-intellij-tool-plugin/send-selection-to-console.png)

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения о кластере больших данных SQL Server и связанных сценариях см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md).

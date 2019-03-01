---
title: Запуск заданий Spark в наборе средств Azure для IntelliJ в кластере SQL Server больших данных
titleSuffix: SQL Server Big Data Clusters
description: Отправка заданий Spark на кластерах SQL Server больших данных в наборе средств Azure для IntelliJ.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.openlocfilehash: 06ce1d325caa0835381fd6f9ecd5428d2bbb6f66
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018480"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-intellij"></a>Отправка заданий Spark на кластерах SQL Server больших данных в IntelliJ

Одним из основных сценариев для больших кластеров данных SQL Server является возможность отправки заданий Spark. Функция отправки задания Spark позволяет отправить локальные файлы JAR-файл или Py со ссылками на кластерах больших данных SQL Server. Он также позволяет выполнять JAR-файл или копировать файлы, которые уже находятся в файловой системе HDFS. 

## <a name="prerequisites"></a>предварительные требования

- Большие данные кластера SQL Server.
- Комплект разработчика Oracle Java. Его можно установить с [веб-сайте Oracle](https://aka.ms/azure-jdks).
- IntelliJ IDEA. Его можно установить с [веб-сайте JetBrains](https://www.jetbrains.com/idea/download/).
- Набор средств Azure для IntelliJ расширения. Инструкции по установке см. в разделе [установка набора средств Azure для IntelliJ](https://docs.microsoft.com/azure/azure-toolkit-for-intellij-installation).

## <a name="link-sql-server-big-data-cluster"></a>Большие данные кластера связи SQL Server
1. Откройте средство IntelliJ IDEA.

2. Если вы используете самозаверяющий сертификат, отключите проверку SSL-сертификата из **средства** меню, выберите **Azure**, **проверки SSL-сертификат кластера Spark**, затем **Отключить**.

    ![Связывание кластера больших данных SQL Server — отключить протокол SSL](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-disableSSL.png)

3. Откройте Azure Explorer из **представление** меню, выберите **средство Windows**, а затем выберите **Azure Explorer**.
4. Щелкните правой кнопкой мыши **кластера больших данных SQL Server**выберите **кластера больших данных связи SQL Server**. Введите **Server**, **имя пользователя**, и **пароль**, затем нажмите кнопку **ОК**.

    ![Связывание кластера больших данных - диалоговое окно](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-dialog.png)

5. Когда откроется диалоговое окно сертификата недоверенном сервера, щелкните **Accept**. Можно управлять сертификатом, в более поздней версии, см. в разделе [сертификаты сервера](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html).

6. Связанный кластер перечислены в разделе **кластера больших данных SQL Server**. Можно отслеживать задания spark, открыв пользовательский Интерфейс журнала spark и пользовательский Интерфейс Yarn, может также удалить связь, щелкнув правой кнопкой мыши в кластере.

    ![Связывание кластера больших данных — контекстное меню](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-contextmenu.png)

## <a name="create-a-spark-scala-application-from-hdinsight-template"></a>Создание приложения Spark Scala из шаблона HDInsight

1. Запустите IntelliJ IDEA и создайте проект. В **новый проект** диалоговое окно, выполните следующие действия: 

   1. Выберите **Azure Spark/HDInsight** > **Spark проект с образцами (Scala)**.

   2. В **инструмент сборки** выберите один из следующих вариантов:

      * **Maven**, для поддержки мастера создания проекта Scala
      * **SBT**, для управления зависимостями и сборки проекта Scala

    ![В диалоговом окне нового проекта](./media/spark-submit-job-intellij-tool-plugin/create-hdi-scala-app.png)

2. Выберите **Далее**.

3. Мастер создания проектов Scala автоматически определяет, установлен ли подключаемый модуль Scala. Выберите пункт **Установить**.

   ![Проверка подключаемого модуля Scala](./media/spark-submit-job-intellij-tool-plugin/Scala-Plugin-check-Reminder.PNG) 

4. Чтобы скачать подключаемый модуль Scala, выберите **ОК**. Следуйте инструкциям, чтобы перезапустить IntelliJ. 

   ![Диалоговое окно установки подключаемого модуля Scala](./media/spark-submit-job-intellij-tool-plugin/Choose-Scala-Plugin.PNG)

5. В **новый проект** окно, выполните следующие действия:  

    ![Выбор пакета SDK для Spark](./media/spark-submit-job-intellij-tool-plugin/hdi-new-project.png)

   1. Введите имя и расположение проекта.

   2. В **пакета SDK проекта** стрелку раскрывающегося списка выберите **Java 1.8** для кластера Spark 2.x или выберите **Java 1.7** для кластера Spark 1.x.

   В. В **версию Spark** стрелку раскрывающегося списка, мастер создания проекта Scala интегрирует правильную версию пакета SDK Spark и пакета SDK для Scala. Если версия кластера Spark ниже 2.0, выберите **Spark 1.x**. В противном случае выберите **Spark2.x**. В этом примере используется **Spark 2.0.2 (Scala 2.11.8)**.

6. Нажмите кнопку **Готово**.

7. Проект Spark автоматически создаст артефакт. Чтобы просмотреть артефакт, сделайте следующее:

   1. На **файл** меню, выберите **структура проекта**.

   2. В **структура проекта** выберите **артефакты** для просмотра по умолчанию артефакт, который создается. Можно также создать собственный артефакт, щелкнув знак «плюс» (**+**).

      ![Сведения об артефакте в диалоговом окне](./media/spark-submit-job-intellij-tool-plugin/default-artifact.png)
      

## <a name="submit-application-to-sql-server-big-data-cluster"></a>Отправьте приложение в кластере SQL Server больших данных
После компоновки больших данных кластера SQL Server вы можете отправить в приложение.

1. Настройте конфигурацию в **конфигураций запуска и отладки** окно, нажмите кнопку + "->"**Apache Spark в SQL Server**, выберите вкладку **удаленно запускать в кластере**, задайте параметры как следующие, затем нажмите кнопку ОК.

    ![Интерактивная консоль добавьте записи конфигурации](./media/spark-submit-job-intellij-tool-plugin/interactive-console-add-config-entry.png)

    ![Связывание кластера больших данных - config](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-config.png)

    * Для **(только Linux) кластеры Spark**, выберите кластер, на котором вы хотите запустить приложение.

    * Выберите артефакт из проекта IntelliJ или с жесткого диска.

    * **Имя класса Main** поля: Значение по умолчанию — основной класс из выбранного файла. Класс можно изменить, выбрав кнопку с многоточием (**...** ) и Выбор другого класса.   

    * **Задание конфигурации** поля:  Как показано выше рисунок задаются значения по умолчанию. Можно изменить значение или добавьте новый ключ/значение для отправки вашего задания. Дополнительные сведения см. в следующих разделах: [Livy Apache REST API](http://livy.incubator.apache.org./docs/latest/rest-api.html)

      ![Значение конфигурации задания поле диалогового окна отправки Spark](./media/spark-submit-job-intellij-tool-plugin/submit-job-configurations.png)

    * **Аргументы командной строки** поля: Можно ввести аргументы значений, разделенных пробелами, для основного класса, при необходимости.

    * **Ссылка на JAR-файлы** и **ссылки на файлы** поля: Можно ввести пути для упоминаемой JAR-файлы и файлы, при наличии. Дополнительные сведения см. в следующих разделах: [Настройка Apache Spark](https://spark.apache.org/docs/latest/configuration.html#runtime-environment) 

      ![Это означает файлы JAR-файл box отправки Spark диалоговое окно](./media/spark-submit-job-intellij-tool-plugin/jar-files-meaning.png)

       > [!NOTE]  
       > Чтобы отправить ссылки на JARs и ссылки на файлы, см.: [Как отправить ресурсов для кластера](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-storage-explorer)
                         
    * **Передача пути**: Можно указать место хранения для отправки ресурсы проекта JAR-файл или Scala. Существует несколько типов хранилищ, которые поддерживаются: **Использовать интерактивный сеанс Spark для отправки** и **WebHDFS использования для отправки**
    
2. Нажмите кнопку **SparkJobRun** Чтобы отправить проект, чтобы выбранном кластере. **Удаленного задания Spark в кластере** вкладка отображает ход выполнения задания в нижней. Можно остановить приложение, щелкнув красную кнопку.  

    ![ссылка больших данных — запуска кластера](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-run.png)

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о больших данных кластера SQL Server и связанные сценарии, см. в разделе [что такое большие данные кластеры SQL Server 2019](big-data-cluster-overview.md)?

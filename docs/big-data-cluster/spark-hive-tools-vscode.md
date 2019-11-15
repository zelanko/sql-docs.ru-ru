---
title: Выполнение заданий Spark с помощью Spark & Hive Tools для VS Code в кластере больших данных SQL Server
titleSuffix: SQL Server big data clusters
description: Отправка задания Spark с помощью Spark & Hive Tools для Visual Studio Code в кластере больших данных SQL Server.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b09a5febe9bc67f04d70c4d5b7850ef26ebac750
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653731"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-cluster-in-visual-studio-code"></a>Отправка заданий Spark в кластере больших данных SQL Server в Visual Studio Code

Вы можете узнать, как с помощью Spark & Hive Tools для Visual Studio Code создавать и отправлять скрипты PySpark для Apache Spark. Сначала мы расскажем, как установить Spark & Hive tools в Visual Studio Code, а затем рассмотрим, как отправлять задания в Spark.  

Spark & Hive Tools можно установить на платформах, поддерживаемых Visual Studio Code, включая Windows, Linux и macOS. Ниже указаны необходимые условия для различных платформ.


## <a name="prerequisites"></a>предварительные требования

Для выполнения действий, описанных в этой статье, необходимо следующее:

- Кластер больших данных SQL Server. См. раздел [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).
- [Visual Studio Code](https://code.visualstudio.com/).
- [Mono](https://www.mono-project.com/docs/getting-started/install/). Mono требуется только для Linux и macOS.
- [Настройка интерактивной среды PySpark для Visual Studio Code](https://docs.microsoft.com/azure/hdinsight/set-up-pyspark-interactive-environment).
- Локальный каталог **SQLBDCexample**.  В этой статье используется **C:\SQLBDC\SQLBDCexample**.

## <a name="install-spark--hive-tools"></a>Установка Spark & Hive Tools

После выполнения предварительных требований можно установить Spark & Hive Tools для Visual Studio Code.  Для этого выполните следующие шаги:

1. Откройте Visual Studio Code.

2. В строке меню выберите **Вид** > **Расширения**.

3. В поле поиска введите **Spark & Hive**.

4. Выберите **Spark & Hive Tools** в результатах поиска и щелкните **Установить**.  

   ![Установка расширения](./media/spark-hive-tools-vscode/extension.png)

5. При необходимости выполните перезагрузку.

## <a name="open-work-folder"></a>Открытие рабочей папки

Выполните следующие действия, чтобы открыть рабочую папку и создать файл в Visual Studio Code:

1. В строке меню выберите **Файл** > **Открыть папку...**  > **C:\SQLBDC\SQLBDCexample**, а затем нажмите кнопку **Выбрать папку**. Папка отображается в представлении **проводника** слева.

2. В представлении **проводника** выберите эту папку, элемент **SQLBDCexample** и значок **Новый файл** рядом с рабочей папкой.

   ![Создание файла](./media/spark-hive-tools-vscode/new-file.png)

3. Присвойте новому файлу имя с расширением `.py` (скрипт Spark).  В этом примере используется **HelloWorld.py**.
4. Скопируйте и вставьте в файл скрипта следующий код:
   ```python
    import sys
    from operator import add
    from pyspark.sql import SparkSession, Row
    
    spark = SparkSession\
        .builder\
        .appName("PythonWordCount")\
        .getOrCreate()
    
    data = [Row(col1='pyspark and spark', col2=1), Row(col1='pyspark', col2=2), Row(col1='spark vs hadoop', col2=2), Row(col1='spark', col2=2), Row(col1='hadoop', col2=2)]
    df = spark.createDataFrame(data)
    lines = df.rdd.map(lambda r: r[0])

    counters = lines.flatMap(lambda x: x.split(' ')) \
        .map(lambda x: (x, 1)) \
        .reduceByKey(add)
    
    output = counters.collect()
    sortedCollection = sorted(output, key = lambda r: r[1], reverse = True)
    
    for (word, count) in sortedCollection:
        print("%s: %i" % (word, count))
   ```

## <a name="link-a-sql-server-big-data-cluster"></a>Связывание кластера больших данных SQL Server

Прежде чем отправлять скрипты в кластеры из Visual Studio Code, нужно связать кластер больших данных SQL Server.

1. В строке меню выберите **Вид** > **Палитра команд...** и введите **Spark / Hive: Link a Cluster** (Связать кластер).

   ![команда связывания кластера](./media/spark-hive-tools-vscode/link-cluster-command.png)

2. Выберите тип связанного кластера **SQL Server Big Data** (Большие данные SQL Server).

3. Введите конечную точку больших данных SQL Server.

4. Введите имя пользователя кластера больших данных SQL Server.

5. Введите пароль для администратора пользователей.

6. Задайте отображаемое имя кластера (необязательно).

7. Выведите список кластеров и просмотрите представление **OUTPUT** для проверки.

## <a name="list-clusters"></a>список кластеров

1. В строке меню выберите **Вид** > **Палитра команд...** и введите **Spark / Hive: List Cluster** (Перечислить кластер).

2. Просмотрите представление **OUTPUT**.  В нем отображаются связанные кластеры.

    ![Настройка конфигурации кластера по умолчанию](./media/spark-hive-tools-vscode/list-cluster-result.png)

## <a name="set-default-cluster"></a>Задание кластера по умолчанию

1. Снова откройте созданную [ранее](#open-work-folder) папку **SQLBDCexample**, если она была закрыта.  

2. Выберите созданный [ранее](#open-work-folder) файл **HelloWorld.py**, чтобы открыть его в редакторе скриптов.

3. Свяжите кластер, если вы еще не сделали этого.

4. Щелкните редактор скриптов правой кнопкой мыши и выберите пункт **Spark/Hive: Set Default Cluster** (Задать кластер по умолчанию).   

5. Выберите кластер в качестве используемого по умолчанию для текущего файла скрипта. Средства автоматически обновляют файл конфигурации **.VSCode\settings.json**. 

   ![Настройка конфигурации кластера по умолчанию](./media/spark-hive-tools-vscode/set-default-cluster-configuration.png)

## <a name="submit-interactive-pyspark-queries"></a>Отправка интерактивных запросов PySpark

Вы можете отправлять интерактивные запросы PySpark, выполнив следующие действия:

1. Снова откройте созданную [ранее](#open-work-folder) папку **SQLBDCexample**, если она была закрыта.  

2. Выберите созданный [ранее](#open-work-folder) файл **HelloWorld.py**, чтобы открыть его в редакторе скриптов.

3. Свяжите кластер, если вы еще не сделали этого.

4. Выберите весь код, щелкните редактор скриптов правой кнопкой мыши и выберите пункт **Spark: PySpark Interactive** (Интерактивная среда PySpark), чтобы отправить запрос, либо используйте сочетание клавиш **CTRL+ALT+I**.

   ![контекстное меню интерактивной среды pyspark](./media/spark-hive-tools-vscode/pyspark-interactive-right-click.png)

5. Выберите кластер, если вы не указали кластер по умолчанию. Через несколько секунд на новой вкладке отображаются результаты **интерактивного окна Python**. Эти средства также позволяют отправить блок кода вместо целого файла скрипта с помощью контекстного меню. 

   ![интерактивная среда pyspark, интерактивное окно python](./media/spark-hive-tools-vscode/pyspark-interactive-python-interactive-window.png) 

6. Введите **"%%info"** и нажмите клавиши **SHIFT+ВВОД** для просмотра сведений о задании. (необязательно)

   ![просмотр сведений о задании](./media/spark-hive-tools-vscode/pyspark-interactive-view-job-information.png)

   > [!NOTE] 
   >
   > Если флажок **Python Extension Enabled** (Расширение Python включено) в параметрах снят (параметр по умолчанию установлен), отправленные результаты интерактивной среды pyspark будут использовать старое окно.
   >
   > ![интерактивная среда pyspark, расширение python отключено](./media/spark-hive-tools-vscode/pyspark-interactive-python-extension-disabled.png)


## <a name="submit-pyspark-batch-job"></a>Отправка пакетного задания PySpark

1. Снова откройте созданную [ранее](#open-work-folder) папку **SQLBDCexample**, если она была закрыта.  

2. Выберите созданный [ранее](#open-work-folder) файл **HelloWorld.py**, чтобы открыть его в редакторе скриптов.

3. Свяжите кластер, если вы еще не сделали этого.

4. Щелкните редактор скриптов правой кнопкой мыши и выберите пункт **Spark: PySpark Batch** (Пакет PySpark), чтобы отправить запрос, либо используйте сочетание клавиш **CTRL+ALT+H**. 

5. Выберите кластер, если вы не указали кластер по умолчанию. После отправки задания Python журналы отправки отображаются в окне **вывода** в Visual Studio Code. Также отображаются **Spark UI URL** (URL-адрес пользовательского интерфейса Spark) и **Yarn UI URL** (URL-адрес пользовательского интерфейса Yarn). Вы можете открыть этот URL-адрес в браузере для отслеживания состояния задания.

   ![Отправка результата задания Python](./media/spark-hive-tools-vscode/submit-pythonjob-result.png) 

## <a name="apache-livy-configuration"></a>Конфигурация Apache Livy

Конфигурация [Apache Livy](https://livy.incubator.apache.org/) поддерживается, и ее можно настроить в файле **.VSCode\settings.json** в папке рабочей области. Сейчас конфигурация Livy поддерживает только скрипт Python. Дополнительные сведения см. в [файле сведений Livy](https://github.com/cloudera/livy/blob/master/README.rst ).

### <a id="triggerlivyconf"></a>**Активация конфигурации Livy**

#### <a name="method-1"></a>Метод 1

1. В строке меню выберите **Файл** > **Настройки** > **Параметры**.  
2. В текстовом поле **Search settings** (Параметры поиска) введите **HDInsight Job Sumission: Livy Conf** (Отправка задания HDInsight: конфигурация Livy).  
3. Выберите **Изменить в settings.json** для соответствующего результата поиска.

#### <a name="method-2"></a>Метод 2.

Отправьте файл и обратите внимание, что папка `.vscode` автоматически добавляется в рабочую папку. Чтобы найти конфигурацию Livy, щелкните `.vscode\settings.json`.

+ Параметры проекта:

    ![Конфигурация Livy](./media/spark-hive-tools-vscode/hdi-livyconfig.png)

>[!NOTE]
>Для параметров **driverMomory** и **executorMomry** задайте значение с единицей измерения, например 1g или 1024m. 

### <a name="supported-livy-configurations"></a>Поддерживаемые конфигурации Livy

#### <a name="post-batches"></a>POST /batches

**Текст запроса**

| name | description | type |
| :- | :- | :- |
| файл | Файл, содержащий приложение для выполнения | путь (обязательно) |
| proxyUser | Пользователь, олицетворяемый при выполнении задания | строка |
| className | Класс main приложения в Java/Spark | строка |
| args | Аргументы командной строки для приложения | список строк |
| jars | Файлы JAR для использования в этом сеансе | список строк |
| pyFiles | Файлы Python для использования в этом сеансе | список строк |
| files | Файлы для использования в этом сеансе | список строк |
| driverMemory | Объем памяти, используемый для процесса драйвера | строка |
| driverCores | Число ядер, используемых для процесса драйвера | INT |
| executorMemory | Объем памяти, используемый для каждого процесса исполнителя | строка |
| executorCores | Число ядер, используемых для каждого исполнителя | INT |
| numExecutors | Число исполнителей, которые должны быть запущены для этого сеанса | INT |
| archives | Архивы для использования в этом сеансе | список строк |
| очередь | Имя очереди YARN, куда выполнена отправка | строка |
| name | Имя сеанса | строка |
| conf | Свойства конфигурации Spark | Сопоставление key=val |

#### <a name="response-body"></a>Текст ответа

Созданный объект пакета.

| name | description | type |
| :- | :- | :- |
| идентификатор | Идентификатор сеанса | INT |
| appId | Идентификатор приложения для этого сеанса | String |
| appInfo | Подробные сведения о приложении | Сопоставление key=val |
| log | Строки журнала | список строк |
| state | Состояние пакета | строка |

>[!NOTE]
>Назначенная конфигурация Livy будет отображена в области вывода при отправке скрипта.

## <a name="additional-features"></a>Дополнительные функции

В Spark & Hive для Visual Studio Code поддерживаются следующие функции:

- **Автозавершение IntelliSense**. Всплывающие предложения для ключевых слов, методов, переменных и т. п. Разные значки представляют различные типы объектов.

    ![Типы объектов IntelliSense в Spark & Hive Tools для Visual Studio Code](./media/spark-hive-tools-vscode/hdinsight-for-vscode-auto-complete-objects.png)
- **Маркер ошибок IntelliSense**. Языковая служба подчеркивает ошибки редактирования для скрипта Hive.     
- **Выделение синтаксиса**. Языковая служба использует разные цвета, чтобы было легче различать переменные, ключевые слова, типы данных, функции и т. п. 

    ![Выделение синтаксиса в Spark & Hive Tools для Visual Studio Code](./media/spark-hive-tools-vscode/hdinsight-for-vscode-syntax-highlights.png)

## <a name="unlink-cluster"></a>Удаление связи кластера

1. В строке меню выберите **Вид** > **Палитра команд...** и введите **Spark / Hive: Unlink a Cluster** (Удалить связь кластера).  

2. Выберите кластер для удаления связи.  

3. Просмотрите представление **OUTPUT** для проверки.  

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения о кластере больших данных SQL Server и связанных сценариях см. в статье [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).

---
title: Выполнение заданий Spark с помощью Spark & средства Hive для VS Code в SQL Server кластера больших данных
titleSuffix: SQL Server big data clusters
description: Отправьте задание Spark с помощью & Hive для Visual Studio Code в SQL Server кластер больших данных.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4458666792d7f4629b4e1820e98e2dbb9901c2b6
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425984"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-cluster-in-visual-studio-code"></a>Отправка заданий Spark в кластере больших данных SQL Server в Visual Studio Code

Узнайте, как с помощью Spark & Hive Tools для Visual Studio Code создавать и отправлять скрипты PySpark для Apache Spark. Сначала мы расскажем, как установить в Visual Studio Code средства Hive, & куст, а затем покажу, как отправлять задания в Spark.  

Средства Spark & Hive можно установить на платформах, которые поддерживаются Visual Studio Code, включая Windows, Linux и macOS. Ниже вы найдете необходимые компоненты для различных платформ.


## <a name="prerequisites"></a>предварительные требования

Для выполнения действий, описанных в этой статье, необходимы следующие элементы.

- SQL Server кластер больших данных. См. [SQL Server кластеры больших данных](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).
- [Visual Studio Code](https://code.visualstudio.com/).
- [Моно](https://www.mono-project.com/docs/getting-started/install/). Mono требуется только для Linux и macOS.
- [Настройка интерактивной среды PySpark для Visual Studio Code](https://docs.microsoft.com/azure/hdinsight/set-up-pyspark-interactive-environment).
- Локальный каталог с именем **хдексампле**.  В этой статье используется **к:\хд\хдексампле**.

## <a name="install-spark--hive-tools"></a>Установка средств Hive & в Spark

После завершения предварительных требований можно установить средства & Hive для Visual Studio Code.  Выполните следующие действия, чтобы установить Spark & средства Hive.

1. Откройте Visual Studio Code.

2. В строке меню перейдите к просмотру  > **расширения**.

3. В поле поиска введите **Spark & Hive**.

4. Выберите **Spark & средства Hive** в результатах поиска и нажмите кнопку **установить**.  

   ![Установить расширение](./media/spark-hive-tools-vscode/extension.png)

5. При необходимости перезагрузите.

## <a name="open-work-folder"></a>Открыть рабочую папку

Выполните следующие действия, чтобы открыть рабочую папку и создать файл в Visual Studio Code.

1. В строке меню выберите **файл** > **Открыть папку...** К:\хд\хдексампле, а затем нажмите кнопку **выбрать папку** .   >  Папка отобразится в представлении **обозревателя** слева.

2. В представлении **проводника** выберите папку **хдексампле**, а затем значок **новый файл** рядом с рабочей папкой.

   ![Создать файл](./media/spark-hive-tools-vscode/new-file.png)

3. Присвойте новому файлу имя с `.py` расширением файла сценария Spark.  В этом примере используется **HelloWorld.py**.
4. Скопируйте и вставьте следующий код в файл скрипта:
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

## <a name="link-a-sql-server-big-data-cluster"></a>Связывание SQL Server кластера больших данных

Прежде чем отправлять скрипты в кластеры из Visual Studio Code, необходимо связать SQL Server кластер больших данных.

1. В строке меню перейдите к разделу **Просмотр** > **палитры команд...** и **введите Spark/Hive: Свяжите кластер**.

   ![Команда "связать кластер"](./media/spark-hive-tools-vscode/link-cluster-command.png)

2. Выберите тип связанного кластера **SQL Server большие данные**.

3. Введите SQL Server конечную точку больших данных.

4. Введите SQL Server имя пользователя кластера больших данных.

5. Введите пароль для администратора пользователя.

6. Задайте отображаемое имя кластера (необязательно).

7. Вывод списка кластеров, просмотр представления **вывода** для проверки.

## <a name="list-clusters"></a>Список кластеров

1. В строке меню перейдите к разделу **Просмотр** > **палитры команд...** и **введите Spark/Hive: Список кластеров**.

2. Просмотрите представление **вывода** .  В представлении отобразятся связанные кластеры.

    ![Настройка конфигурации кластера по умолчанию](./media/spark-hive-tools-vscode/list-cluster-result.png)

## <a name="set-default-cluster"></a>Задать кластер по умолчанию

1. Повторно откройте папку **хдексампле** , созданную [ранее](#open-work-folder) , если она была закрыта.  

2. Выберите файл **HelloWorld.py** , созданный [ранее](#open-work-folder) , и он откроется в редакторе скриптов.

3. Свяжите кластер, если вы еще не сделали этого.

4. Щелкните правой кнопкой мыши редактор скриптов и выберите **Spark/Hive: Задать кластер**по умолчанию.   

5. Выберите кластер в качестве кластера по умолчанию для текущего файла скрипта. Средства автоматически обновляют файл конфигурации **. Вскоде\сеттингс.жсон**. 

   ![Настройка конфигурации кластера по умолчанию](./media/spark-hive-tools-vscode/set-default-cluster-configuration.png)

## <a name="submit-interactive-pyspark-queries"></a>Отправка интерактивных запросов PySpark

Вы можете отправлять Интерактивные запросы PySpark, выполнив следующие действия:

1. Повторно откройте папку **хдексампле** , созданную [ранее](#open-work-folder) , если она была закрыта.  

2. Выберите файл **HelloWorld.py** , созданный [ранее](#open-work-folder) , и он откроется в редакторе скриптов.

3. Свяжите кластер, если вы еще не сделали этого.

4. Выберите весь код и щелкните правой кнопкой мыши редактор скриптов, выберите **Spark: PySpark интерактивный** , чтобы отправить запрос, или используйте сочетание **клавиш CTRL + ALT + I**.

   ![Интерактивное контекстное меню pyspark](./media/spark-hive-tools-vscode/pyspark-interactive-right-click.png)

5. Выберите кластер, если вы не указали кластер по умолчанию. Через несколько секунд Интерактивные результаты **Python** отобразятся на новой вкладке. Средства также позволяют отправить блок кода вместо всего файла скрипта с помощью контекстного меню. 

   ![интерактивное окно Python pyspark Interactive](./media/spark-hive-tools-vscode/pyspark-interactive-python-interactive-window.png) 

6. Введите **"%% info"** , а затем нажмите клавиши **SHIFT + ВВОД** , чтобы просмотреть сведения о задании. (необязательно)

   ![Просмотр сведений о задании](./media/spark-hive-tools-vscode/pyspark-interactive-view-job-information.png)

   > [!NOTE] 
   >
   > Если **расширение Python включено** в параметрах (параметр по умолчанию установлен), отправленные результаты взаимодействия pyspark будут использовать старое окно.
   >
   > ![Расширенное интерактивное расширение Python pyspark отключено](./media/spark-hive-tools-vscode/pyspark-interactive-python-extension-disabled.png)


## <a name="submit-pyspark-batch-job"></a>Отправка пакетного задания PySpark

1. Повторно откройте папку **хдексампле** , созданную [ранее](#open-work-folder) , если она была закрыта.  

2. Выберите файл **HelloWorld.py** , созданный [ранее](#open-work-folder) , и он откроется в редакторе скриптов.

3. Свяжите кластер, если вы еще не сделали этого.

4. Щелкните правой кнопкой мыши редактор скриптов и выберите **Spark: PySpark пакет**или используйте сочетание клавиш **CTRL + ALT + H**. 

5. Выберите кластер, если вы не указали кластер по умолчанию. После отправки задания Python журналы отправки отображаются в окне **вывод** в Visual Studio Code. Также отображаются **URL-адрес пользовательского интерфейса Spark** и **URL-адрес пользовательского интерфейса Yarn** . Можно открыть URL-адрес в браузере для наблюдения за состоянием задания.

   ![Отправить результат задания Python](./media/spark-hive-tools-vscode/submit-pythonjob-result.png) 

## <a name="apache-livy-configuration"></a>Настройка Apache Livy

Конфигурация [Apache Livy](https://livy.incubator.apache.org/) поддерживается, ее можно задать в **. Вскоде\сеттингс.жсон** в папке рабочего пространства. В настоящее время Конфигурация Livy поддерживает только скрипт Python. Дополнительные сведения см. в [файле readme Livy](https://github.com/cloudera/livy/blob/master/README.rst ).

### <a id="triggerlivyconf"></a>**Как активировать конфигурацию Livy**

#### <a name="method-1"></a>Метод 1

1. В строке меню выберите **файл** >  > **настройки параметры**.  
2. В текстовом поле **Search Settings (параметры поиска** ) введите **сумиссион задание HDInsight: Livy CONF**.  
3. Выберите **изменить в Settings. JSON** для соответствующего результата поиска.

#### <a name="method-2"></a>Метод 2.

Отправить файл. Обратите внимание `.vscode` , что папка автоматически добавляется в рабочую папку. Чтобы найти конфигурацию Livy, щелкните `.vscode\settings.json`.

+ Параметры проекта:

    ![Конфигурация Livy](./media/spark-hive-tools-vscode/hdi-livyconfig.png)

>[!NOTE]
>Для параметров **дривермомори** и **ексекутормомри**задайте значение Unit, например 1 ГБ или 1024m. 

### <a name="supported-livy-configurations"></a>Поддерживаемые конфигурации Livy

#### <a name="post-batches"></a>ОПУБЛИКОВАТЬ/батчес

**Текст запроса**

| name | description | type |
| :- | :- | :- |
| файл | Файл, содержащий приложение для выполнения | путь (обязательно) |
| proxyUser | Пользователь, использующий олицетворение при выполнении задания | строка |
| className | Класс Main приложения Java/Spark | строка |
| args | Аргументы командной строки для приложения | список строк |
| JAR | JAR для использования в этом сеансе | Список строк |
| pyFiles | Файлы Python для использования в этом сеансе | Список строк |
| files | файлы, используемые в этом сеансе | Список строк |
| дривермемори | Объем памяти, используемый для процесса драйвера | строка |
| дриверкорес | Число ядер, используемых для процесса драйвера | ssNoversion |
| ексекутормемори | Объем памяти, используемый для каждого процесса исполнителя | строка |
| ексекуторкорес | Число ядер, используемых для каждого исполнителя | ssNoversion |
| нумексекуторс | Число исполнителей, которые должны быть запущены для этого сеанса | ssNoversion |
| копии | Архивы для использования в этом сеансе | Список строк |
| queue | Имя очереди YARN, в которую Отправлено | строка |
| name | Имя этого сеанса | строка |
| дает | Свойства конфигурации Spark | Map ключевого = Val |

#### <a name="response-body"></a>Текст ответа

Созданный объект пакета.

| name | description | type |
| :- | :- | :- |
| id | Идентификатор сеанса | ssNoversion |
| ИД | Идентификатор приложения для этого сеанса | String |
| Маркеров | Подробные сведения о приложении | Map ключевого = Val |
| Журналь | Строки журнала | список строк |
| state | Состояние пакета | строка |

>[!NOTE]
>Назначенная конфигурация Livy будет отображаться в области вывода при отправке скрипта.

## <a name="additional-features"></a>Дополнительные возможности

В Spark & Hive для Visual Studio Code поддерживаются следующие функции.

- **Автозаполнение IntelliSense**. Всплывающие предложения для ключевого слова, методов, переменных и т. д. Разные значки представляют различные типы объектов.

    ![Spark & средства Hive для Visual Studio Code типов объектов IntelliSense](./media/spark-hive-tools-vscode/hdinsight-for-vscode-auto-complete-objects.png)
- **Маркер ошибки IntelliSense**. Языковая служба подчеркивает ошибки редактирования для скрипта Hive.     
- Подсветка синтаксиса. Языковая служба использует разные цвета для различения переменных, ключевых слов, типов данных, функций и т. д. 

    ![В Spark & средства Hive для Visual Studio Code выделение синтаксиса](./media/spark-hive-tools-vscode/hdinsight-for-vscode-syntax-highlights.png)

## <a name="unlink-cluster"></a>Отменить связь кластера

1. В строке меню перейдите к разделу **Просмотр** > **палитры команд...** , а **затем введите Spark/Hive: Удалить связь с кластером**.  

2. Выберите кластер для разрыва связи.  

3. Просмотр представления **вывода** для проверки.  

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о SQL Server кластере больших данных и связанных сценариях см. в разделе [SQL Server кластеры больших данных](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).

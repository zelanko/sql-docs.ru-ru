---
title: Запуск заданий Spark в Azure Data Studio
titleSuffix: SQL Server 2019 big data clusters
description: Отправка заданий Spark в кластерах больших данных SQL Server в Azure Data Studio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c1d439c13b06b305c814813eeca7cb9bf8aa53c5
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57578244"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-azure-data-studio"></a>Отправка заданий Spark в кластерах больших данных SQL Server в Azure Data Studio

Одним из основных сценариев для работы с большими данными кластеров является возможность отправки заданий Spark для предварительной версии SQL Server 2019. Функция отправки задания Spark позволяет отправить локальные файлы JAR-файл или Py со ссылками на кластер SQL Server 2019 больших данных. Он также позволяет выполнять JAR-файл или копировать файлы, которые уже находятся в файловой системе HDFS. 

## <a name="prerequisites"></a>предварительные требования

- [Средства SQL Server 2019 больших данных](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

- [Подключение Azure Data Studio к шлюзу HDFS/Spark кластера больших данных](connect-to-big-data-cluster.md).

## <a name="open-spark-job-submission-dialog"></a>Открыть диалоговое окно отправки задания Spark
Существует несколько способов, чтобы открыть диалоговое окно отправки задания Spark. Способы включают панели мониторинга, контекстное меню в обозревателе объектов и Palate команды.

+ Нажмите кнопку **новое задание Spark** на панели мониторинга, чтобы открыть диалоговое окно отправки задания Spark.

    ![Отправьте меню, нажав панель мониторинга](./media/submit-spark-job/new-spark-job.png)
 
+ Щелкните правой кнопкой мыши в кластере, в обозревателе объектов и выберите **отправить задание Spark** в контекстном меню. Откроется диалоговое окно отправки задания Spark.  
 
    ![Отправьте меню, щелкните правой кнопкой мыши кластер](./media/submit-spark-job/submit-spark-job.png)

+ Щелкните правой кнопкой мыши на файле Jar/Py в обозревателе объектов и выберите **отправить задание Spark** в контекстном меню. Откроется диалоговое окно отправки задания Spark с полем Jar/Py заранее заполнить. 
 
    ![Отправить меню, щелкните правой кнопкой мыши файл](./media/submit-spark-job/submit-spark-job-2.png)

+ Используйте команду **отправить задание Spark** палитре команд введите сочетание клавиш Ctrl + Shift + P (в Windows) и Cmd + Shift + P (в Mac).

    ![Отправить палитру команд меню в windows](./media/submit-spark-job/submit-spark-job-3.png)

    ![Отправить палитру команд меню в mac](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>Отправка задания Spark 
Диалоговое окно отправки задания Spark отображается следующим образом. Введите имя задания, путь к файлу JAR/Py, основной класс и остальные поля. JAR-файл / источник Py-файл может быть с локального компьютера или из HDFS. Если у задания Spark ссылаются на JAR-файлы, копировать файлы или дополнительные файлы, нажмите кнопку **ДОПОЛНИТЕЛЬНО** вкладку и введите соответствующие пути к файлам. Нажмите кнопку **отправить** для отправки задания Spark.
 
![Диалоговое окно создания задания spark](./media/submit-spark-job/submit-spark-job-section.png)

![Диалоговое окно с дополнительными](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>Мониторинг отправки заданий Spark
После отправки задания Spark, Spark задания отправки и выполнения сведения о состоянии отображаются в журнале задания в левой части. И сведения о хода выполнения и журналов, также отображаются в **ВЫВОДА** нижней части окна.
+ Задание Spark во время выполнения, **журнал задач** панели и **ВЫВОДА** окна с помощью процесса обновления.

![Мониторинг выполняющегося задания spark](./media/submit-spark-job/monitor-spark-job-submission.png)

+ Когда задание Spark находится в завершено успешно, вы увидите ссылки пользовательского интерфейса Spark и пользовательский Интерфейс Yarn в **ВЫВОДА** окна. Можно щелкнуть ссылки на дополнительные сведения.

![Ссылка на задание Spark в выходных данных](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о больших данных кластера SQL Server и связанные сценарии, см. в разделе [что такое большие данные кластера SQL Server](big-data-cluster-overview.md)?


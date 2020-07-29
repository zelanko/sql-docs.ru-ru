---
title: Отправка заданий Spark. Azure Data Studio
titleSuffix: SQL Server Big Data Clusters
description: Отправка заданий Spark в кластере больших данных SQL Server в Azure Data Studio.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0deca0c189782e56fdbb37dd388fa9b55982991f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726713"
---
# <a name="submit-spark-jobs-on-big-data-clusters-2019-in-azure-data-studio"></a>Отправка заданий Spark на [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Azure Data Studio

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Одним из основных сценариев для кластеров больших данных является возможность отправки заданий Spark для SQL Server. Функция отправки заданий Spark позволяет отправлять локальные файлы JAR или PY со ссылками на кластер больших данных SQL Server 2019. Она также позволяет выполнять файлы JAR или PY, которые уже находятся в файловой системе HDFS. 

## <a name="prerequisites"></a>Предварительные требования

- [Средства для работы с большими данными SQL Server 2019](deploy-big-data-tools.md)
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

- [Подключите Azure Data Studio к шлюзу HDFS/Spark кластера больших данных](connect-to-big-data-cluster.md).

## <a name="open-spark-job-submission-dialog"></a>Открытие диалогового окна отправки заданий Spark

Диалоговое окно отправки заданий Spark можно открыть несколькими способами. К ним относятся панель мониторинга, контекстное меню в обозревателе объектов и палитра команд.

- Чтобы открыть диалоговое окно отправки заданий Spark, щелкните **Создать задание Spark** на панели мониторинга.

    ![Открытие меню отправки посредством щелчка на панели мониторинга](./media/submit-spark-job/new-spark-job.png)

- Либо щелкните правой кнопкой мыши кластер в обозревателе объектов и выберите пункт **Отправить задание Spark** в контекстном меню.

    ![Открытие меню отправки из контекстного меню файла](./media/submit-spark-job/submit-spark-job-1.png)


- Чтобы открыть диалоговое окно отправки заданий Spark с предварительно заполненными полями JAR/PY, щелкните правой кнопкой мыши файл JAR/PY в обозревателе объектов и выберите пункт **Отправить задание Spark** в контекстном меню.  

    ![Открытие меню отправки из контекстного меню кластера](./media/submit-spark-job/submit-spark-job.png)

- Используйте элемент **Отправить задание Spark** из палитры команд, нажав клавиши **CTRL+SHIFT+P** (в Windows) и **CMD+SHIFT+P** (в Mac).

    ![Открытие меню отправки из палитры команд в Windows](./media/submit-spark-job/submit-spark-job-3.png)

    ![Открытие меню отправки из палитры команд в Mac](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>Отправка задания Spark 

Диалоговое окно отправки заданий Spark отображается в указанном ниже виде. Заполните имя задания, путь к файлу JAR/PY, основной класс и другие поля. Источником файла JAR/PY может быть локальная файловая система или HDFS. Если задание Spark содержит ссылки на файлы JAR, PY или другие, перейдите на вкладку **Дополнительно** и введите соответствующие пути к файлам. Нажмите кнопку **Отправить**, чтобы отправить задание Spark.

![Диалоговое окно создания задания Spark](./media/submit-spark-job/submit-spark-job-section.png)

![Диалоговое окно "Дополнительно"](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>Мониторинг отправки задания Spark

После отправки задания Spark сведения о состоянии его отправки и выполнения отображаются в журнале задач слева. Сведения о ходе выполнения и журналах также отображаются в окне **Вывод** внизу.

- По мере выполнения задания Spark панель **Журнал задач** и окно **Вывод** обновляются.

    ![Мониторинг выполняющегося задания Spark](./media/submit-spark-job/monitor-spark-job-submission.png)

- После успешного завершения задания Spark в окне **Вывод** отображаются ссылки пользовательского интерфейса Spark и Yarn. Щелкните эти ссылки для получения дополнительных сведений.

    ![Ссылка на задание Spark в выходных данных](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластере больших данных SQL Server и связанных сценариях см. в статье [Что такое кластеры больших данных SQL Server?](big-data-cluster-overview.md)

---
title: Запуск примера записной книжки с помощью Spark
titleSuffix: SQL Server big data clusters
description: В этом учебнике демонстрируется загрузка и запуск примера записной книжки Spark в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 03/30/2020
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6961dd76f35316dbd3923bb24849011a20f184c0
ms.sourcegitcommit: ef20f39a17fd4395dd2dd37b8dd91b57328a751c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92793741"
---
# <a name="run-a-sample-notebook-using-spark"></a>Запуск примера записной книжки с помощью Spark

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этом руководстве демонстрируется загрузка и запуск записной книжки Azure Data Studio в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Такой подход позволяет специалистам по обработке и анализу данных выполнять код Python, R или Scala в кластере.

> [!TIP]
> При необходимости вы можете скачать и выполнить скрипт, содержащий команды из этого руководства. См. инструкции в [примерах Spark](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) на сайте GitHub.

## <a name="prerequisites"></a><a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка примера данных в кластер больших данных](tutorial-load-sample-data.md)

## <a name="download-the-sample-notebook-file"></a>Скачивание файла с примером записной книжки

Чтобы загрузить файл с примером записной книжки **spark-sql.ipynb** в Azure Data Studio, выполните следующие инструкции.

1. Откройте командную строку Bash (Linux) или Windows PowerShell.

1. Перейдите в каталог, в который требуется скачать файл с примером записной книжки.

1. Выполните следующую команду **curl** , чтобы скачать файл с записной книжкой с сайта GitHub:

   ```bash
   curl https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-loading/transform-csv-files.ipynb -o transform-csv-files.ipynb
   ```

## <a name="open-the-notebook"></a>Открытие записной книжки

Выполните следующие действия, чтобы открыть файл с записной книжкой в Azure Data Studio:

1. В Azure Data Studio установите подключение к главному экземпляру в кластере больших данных. Дополнительные сведения см. в разделе [Подключение к кластеру больших данных](connect-to-big-data-cluster.md).

1. Дважды щелкните подключение шлюза HDFS/Spark в окне **Серверы** . Выберите **Открыть записную книжку** .

   ![Открытие записной книжки](media/notebook-tutorial-spark/azure-data-studio-open-notebook.png)

1. Дождитесь, пока будет заполнено поле **Ядро** и задан целевой контекст ( **Присоединить к** ). В поле **Ядро** укажите **PySpark3** , а в поле **Присоединить к** введите IP-адрес конечной точки вашего кластера больших данных.

   ![Заполнение полей "Ядро" и "Присоединить к"](media/notebook-tutorial-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Запуск ячеек записной книжки

Чтобы запустить любую ячейку записной книжки, нажмите расположенную слева от нее кнопку воспроизведения. После того как выполнение ячейки будет завершено, в записной книжке будут показаны результаты.

![Запуск ячейки записной книжки](media/notebook-tutorial-spark/run-notebook-cell.png)

Последовательно запустите все ячейки в примере записной книжки. Дополнительные сведения об использовании записных книжек с [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующих статьях:

- [Как использовать записные книжки](../azure-data-studio/notebooks/notebooks-guidance.md)
- [Как управлять записными книжками в Azure Data Studio](notebooks-manage-bdc.md)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках:
> [!div class="nextstepaction"]
> [Как использовать записные книжки](../azure-data-studio/notebooks/notebooks-guidance.md)
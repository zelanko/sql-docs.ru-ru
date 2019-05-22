---
title: Запуск записной книжки образец | Документация Майкрософт
titleSuffix: SQL Server big data clusters
description: В этом руководстве показано, как загрузить образец notebook Spark в кластере SQL Server 2019 больших данных (Предварительная версия) выполнения.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ed1516c14a8a49269ea0768a2ddafb9e255c24a9
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994145"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-big-data-cluster"></a>Учебник. Запуск записной книжки пример работы с большими данными в кластере SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Этом руководстве показано, как загрузить и выполнить записную книжку в студии данных Azure в кластере SQL Server 2019 больших данных (Предварительная версия). Благодаря этому специалисты по анализу данных и инженеры данных, для выполнения кода Python, R или Scala для кластера.

> [!TIP]
> При желании можно загрузить и запустить сценарий для команды в этом руководстве. Инструкции см. в разделе [Spark примеры](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) на сайте GitHub.

## <a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка образца данных в кластере больших данных](tutorial-load-sample-data.md)

## <a name="download-the-sample-notebook-file"></a>Скачать пример файла записной книжки

Используйте следующие инструкции для загрузки файла примера записной книжки **spark sql.ipynb** студия данных Azure.

1. Откройте командную строку bash (Linux) или Windows PowerShell.

1. Перейдите в каталог, где вы хотите скачать пример файла записной книжки для.

1. Выполните следующую команду, **curl** команду, чтобы скачать файл записной книжки из GitHub:

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-loading/transform-csv-files.ipynb' -o transform-csv-files.ipynb
   ```

## <a name="open-the-notebook"></a>Открыть записную книжку

Ниже показано, как открыть файл записной книжки в Azure Data Studio:

1. В Azure Data Studio подключитесь к основной экземпляр кластера больших данных. Дополнительные сведения см. в разделе [подключение к кластеру больших данных](connect-to-big-data-cluster.md).

1. Дважды щелкните подключение шлюза HDFS или Spark в **серверы** окна. Затем выберите **открыть записную книжку**.

   ![Открыть записную книжку](media/tutorial-notebook-spark/azure-data-studio-open-notebook.png)

1. Дождитесь **ядра** и целевого контекста (**присоединить к**) для заполнения. Задайте **ядра** для **PySpark3**и задайте **присоединить к** на IP-адрес конечной точки кластера больших данных.

   ![Ядро задается и присоединить к](media/tutorial-notebook-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Выполнять ячейки записной книжки

Каждая ячейка записной книжки можно запустить, нажав кнопку воспроизведения слева от ячейки. Результаты отображаются в записной книжке, после завершения ячейки.

![Запустите ячейку записной книжки](media/tutorial-notebook-spark/run-notebook-cell.png)

Выполните каждую ячейку в записной книжке образец подряд. Дополнительные сведения об использовании записных книжек с кластерами больших данных в SQL Server см. следующие ресурсы:

- [Как использовать записные книжки в предварительной версии SQL Server 2019](notebooks-guidance.md)
- [Как управлять записными книжками в Azure Data Studio](notebooks-how-to-manage.md)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о записных книжек:
> [!div class="nextstepaction"]
> [Дополнительные сведения о записных книжек](notebooks-guidance.md)

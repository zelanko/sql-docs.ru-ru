---
title: Записные книжки с ядром Kusto в Azure Data Studio
description: В этом учебнике показано, как создать и запустить записную книжку Kusto.
ms.topic: how-to
ms.prod: azure-data-studio
ms.technology: azure-data-studio
author: markingmyname
ms.author: maghan
ms.reviewer: jukoesma
ms.custom: ''
ms.date: 09/22/2020
ms.openlocfilehash: 416fd5aabb07db3deed1d4d78769249a99113216
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379599"
---
# <a name="create-and-run-a-kusto-kql-notebook-preview"></a>Создание и запуск записной книжки Kusto (KQL) (предварительная версия)

В этой статье показано, как создать и запустить [записную книжку Azure Data Studio](./notebooks-guidance.md) с помощью [расширения Kusto (KQL)](../extensions/kusto-extension.md), подключившись к кластеру Azure Data Explorer.

С помощью расширения Kusto (KQL) можно изменить параметр ядра на **Kusto**.

Эта функция в настоящее время находится на стадии предварительной версии.

## <a name="prerequisites"></a>Предварительные требования

Если у вас еще нет подписки Azure, создайте [бесплатную учетную запись](https://azure.microsoft.com/free/) Azure, прежде чем начинать работу.

- [Кластер Azure Data Explorer с базой данных, к которой можно подключаться](https://docs.microsoft.com/azure/data-explorer/create-cluster-database-portal).
- [Azure Data Studio](../download-azure-data-studio.md).
- [Расширение Kusto (KQL) для Azure Data Studio](../extensions/kusto-extension.md).

## <a name="create-a-kusto-kql-notebook"></a>Создание записной книжки Kusto (KQL)

Выполните следующие действия, чтобы создать файл записной книжки в Azure Data Studio:

1. В Azure Data Studio подключитесь к кластеру Azure Data Explorer.

2. Перейдите в панель **Подключения**, в окне **Серверы** щелкните правой кнопкой мыши базу данных Kusto и выберите *Создать записную книжку*. Вы также можете выбрать **Файл** > **Создать записную книжку**.

   :::image type="content" source="media/notebooks-kusto-kernel/kusto-new-notebook.png" alt-text="Открытие записной книжки":::

3. В качестве **ядра** выберите *Kusto*. Убедитесь, что в меню **Подключиться к** задано имя кластера и база данных. В этой статье мы используем кластер help.kusto.windows.net с данными базы данных Samples.

   :::image type="content" source="media/notebooks-kusto-kernel/set-kusto-kernel.png" alt-text="Открытие записной книжки":::

Вы можете сохранить записную книжку с помощью команды **Сохранить** или **Сохранить как...** в меню **Файл**.

Чтобы открыть записную книжку, можно использовать команду **Открыть файл...** в меню **Файл**, выбрать **Открыть файл** на странице **приветствия** или использовать команду **Файл: открыть** в палитре команд.

## <a name="change-the-connection"></a>Изменение подключения

Чтобы изменить подключение Kusto для записной книжки, выполните следующие действия.

1. Выберите меню **Присоединить к** на панели инструментов записной книжки, а затем выберите **Изменить подключение**.

   :::image type="content" source="media/notebooks-kusto-kernel/kusto-select-attach-to-change-connections.png" alt-text="Открытие записной книжки":::

   > [!Note]
   > Убедитесь, что поле базы данных заполнено. Для записных книжек Kusto требуется указать базу данных.

2. Теперь можно выбрать последний сервер, использованный для подключения, или ввести сведения о новом подключении.

   :::image type="content" source="media/notebooks-kusto-kernel/kusto-change-connection-cluster.png" alt-text="Открытие записной книжки":::

   > [!Note]
   > Укажите имя кластера без `https://`.

## <a name="run-a-code-cell"></a>Выполнение ячейки кода

Вы можете создавать ячейки, содержащие запросы KQL, которые можно запускать на месте, нажав кнопку **Выполнить ячейку** слева от ячейки. После завершения выполнения ячейки результаты будут показаны в записной книжке.

Пример:

1. Добавьте новую ячейку кода, выбрав команду **+Код** на панели инструментов.

   :::image type="content" source="media/notebooks-kusto-kernel/kusto-kernel-code.png" alt-text="Открытие записной книжки":::

2. Скопируйте приведенный ниже пример, вставьте его в ячейку и нажмите **Выполнить ячейку**. Этот пример запрашивает данные StormEvents для определенного типа события.

   ```kusto
    StormEvents
    | where EventType == "Waterspout"
   ```

   :::image type="content" source="media/notebooks-kusto-kernel/run-kusto-notebook-cell.png" alt-text="Открытие записной книжки":::

## <a name="save-the-result-or-show-chart"></a>Сохранение результата или отображение диаграммы

При выполнении скрипта, возвращающего результат, этот результат можно сохранить в разных форматах с помощью панели инструментов, отображаемой над результатом.

- Сохранить в формате CSV
- Сохранить в формате Excel
- Сохранить в формате JSON
- Сохранить в формате XML
- Показать диаграмму

```kusto
    StormEvents
    | limit 10
```

:::image type="content" source="media/notebooks-kusto-kernel/run-notebook-save-results.png" alt-text="Открытие записной книжки":::

## <a name="known-issues"></a>Известные проблемы

| Сведения | Обходной путь |
|---------|------------|
| [В результате запроса отображаются только заголовки столбцов](https://github.com/microsoft/azuredatastudio/issues/12565). | Н/Д |

Можно отправить [запрос функции](https://github.com/microsoft/azuredatastudio/issues/new?assignees=&labels=&template=feature_request.md&title=), чтобы оставить отзыв для команды специалистов по продукту.  
Можно сообщить об [ошибке](https://github.com/microsoft/azuredatastudio/issues/new?assignees=&labels=&template=bug_report.md&title=), чтобы оставить отзыв для команды специалистов по продукту.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках:

- [Расширение Kusto (KQL) для Azure Data Studio](../extensions/kusto-extension.md)
- [Использование записных книжек в Azure Data Studio](../notebooks-guidance.md)
- [Создание и запуск записной книжки Python](../notebooks-tutorial-python-kernel.md)
- [Создание и запуск записной книжки SQL Server](../notebooks-tutorial-sql-kernel.md)

---
title: Управление. Записные книжки Azure Data Studio
titleSuffix: SQL Server Big Data Clusters
description: Используйте записную книжку из Azure Data Studio для управления Кластерами больших данных SQL Server и устранения их неполадок.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 03/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9020f8745c22a9e6382b6538d5bf650c17e923e4
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196128"
---
# <a name="manage-sql-server-big-data-clusters-with-azure-data-studio-notebooks"></a>Управление Кластерами больших данных SQL Server с помощью записных книжек Azure Data Studio

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет расширение для Azure Data Studio, включающее в себя записные книжки. Записная книжка предоставляет документацию и код, которые можно использовать в Azure Data Studio для управления Кластерами больших данных SQL Server 2019.

[Записные книжки](../azure-data-studio/notebooks/notebooks-guidance.md), которые изначально были реализованы как проект с открытым кодом, теперь включены в [Azure Data Studio](../azure-data-studio/download-azure-data-studio.md). Вы можете использовать разметку Markdown для текста в текстовых ячейках и одно из доступных ядер для написания кода в ячейках кода.

С помощью записных книжках можно развертывать кластеры больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Помимо стандартных записных книжек, вы можете просмотреть коллекцию записных книжек, называемых книгами Jupyter. Книга Jupyter содержит оглавление для навигации по коллекции записных книжек, что позволяет легко найти требуемую записную книжку для устранения неполадок SQL Server или просмотра состояния кластера.

## <a name="prerequisites"></a>Предварительные требования

Для открытия записной книжки необходимы следующие компоненты:

* последняя версия [Azure Data Studio](../azure-data-studio/download-azure-data-studio.md);
* расширение [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], установленное в Azure Data Studio.

Помимо этих компонентов, для развертывания Кластеров больших данных SQL Server 2019 требуется следующее:

* [azdata](../azdata/install/deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="access-troubleshooting-notebooks"></a>Доступ к записным книжкам для устранения неполадок

Получить доступ к записным книжкам для устранения неполадок можно тремя способами.

### <a name="command-palette"></a>Палитра команд

1. Выберите элемент **Вид** > **Палитра команд** .

2. Введите **Книги Jupyter: руководство для SQL Server 2019** .

Откроется мини-приложение "Книги Jupyter" с книгой Jupyter, содержащей записные книжки для устранения неполадок, связанных с Кластерами больших данных SQL Server.

### <a name="sql-master-dashboard"></a>Главная панель мониторинга SQL

1. После установки Azure Data Studio для участников программы предварительной оценки подключитесь к экземпляру Кластеров больших данных SQL Server.

2. Подключившись к экземпляру, щелкните правой кнопкой мыши имя сервера в разделе **Подключения** и выберите пункт **Управление** .

3. На панели мониторинга выберите **Кластер больших данных SQL Server** . Выберите **руководство по SQL Server 2019** , чтобы открыть книгу Jupyter с нужными записными книжками.
    ![Записные книжки Jupyter на панели мониторинга](media/manage-notebooks/jupyter-book-button.png)

4. Выберите записную книжку, соответствующую нужной задаче.

### <a name="controller-dashboard"></a>Информационная панель контроллера

1. В представлении **Подключения** разверните раздел **Кластеры больших данных SQL Server** .

2. Добавьте сведения о конечной точке контроллера.

3. Подключившись к контроллеру, щелкните правой кнопкой мыши конечную точку и выберите пункт **Управление** .

4. После загрузки панели мониторинга выберите **Устранение неполадок** , чтобы открыть руководства по устранению неполадок в книге Jupyter.

## <a name="use-troubleshooting-notebooks"></a>Использование записных книжек для устранения неполадок

1. Найдите нужное руководство по устранению неполадок в оглавлении книги Jupyter.

2. Записные книжки оптимизированы, поэтому нужно просто выбрать **Запустить ячейки** . Это действие будет выполнять каждую ячейку в записной книжке по отдельности, пока записная книжка не завершится.

3. При обнаружении ошибки книга Jupyter предложит записную книжку для ее устранения. Выполните рекомендуемые действия и снова запустите записную книжку.

## <a name="change-the-big-data-cluster"></a>Изменение кластера больших данных

Чтобы изменить кластер больших данных SQL Server для записной книжки, сделайте следующее.

1. На панели инструментов записной книжки щелкните меню **Присоединить к** .

   ![На панели инструментов записной книжки щелкните меню "Присоединить к"](./media/notebooks-how-to-manage/select-attach-to-1.png)

2. Выберите сервер в меню **Присоединить к** .

   ![Выберите сервер в меню "Присоединить к"](./media/notebooks-how-to-manage/select-attach-to-2.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках в Azure Data Studio см. в статье [Использование записных книжек в SQL Server](../azure-data-studio/notebooks/notebooks-guidance.md).
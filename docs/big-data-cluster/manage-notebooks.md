---
title: Управление кластером больших данных SQL Server с помощью записных книжек Azure Data Studio
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Используйте записную книжку из Azure Data Studio для управления кластером больших данных и устранения его неполадок.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7adc5c3d07b47b5310d8a45d00747d6dd6de9952
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028585"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Управление кластерами больших данных SQL Server с помощью записных книжек Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет расширение для Azure Data Studio, включающее в себя записные книжки. Записная книжка содержит документацию и код, которые можно использовать в Azure Data Studio для управления кластерами больших данных SQL Server.

[Записные книжки](notebooks-guidance.md), которые изначально были реализованы как проект с открытым кодом, теперь интегрированы в [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download). Вы можете использовать разметку Markdown для текста в текстовых ячейках и одно из доступных ядер для написания кода в ячейках кода.

С помощью записных книжках можно развертывать кластеры больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Помимо записных книжек, пользователи могут просматривать набор записных книжек, которые называются книгами Jupyter. Книга Jupyter содержит оглавление для навигации по коллекции записных книжек, что позволяет пользователю легко найти требуемую записную книжку для устранения неполадок SQL Server или просмотра состояния кластера.

## <a name="prerequisites"></a>предварительные требования

Для запуска записной книжки требуются следующие компоненты:

* последняя [сборка Azure Data Studio для участников программы предварительной оценки](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master);
* расширение [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], установленное в Azure Data Studio.

Помимо перечисленных выше компонентов, для развертывания кластера больших данных SQL Server 2019 требуется следующее:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>Доступ к записным книжкам для устранения неполадок

1. После установки Azure Data Studio для участников программы предварительной оценки подключитесь к экземпляру кластера больших данных SQL Server.
2. После успешного подключения щелкните правой кнопкой мыши имя сервера в мини-приложении "Подключения" и выберите пункт **Управление**.
3. На панели мониторинга щелкните **Кластер больших данных SQL Server**. Щелкните **руководство по SQL Server 2019**, чтобы открыть книгу Jupyter с нужными записными книжками.
    ![кнопка](media/manage-notebooks/jupyter-book-button.png)

1. В окне выбора папки выберите расположение, в котором нужно сохранить книгу Jupyter.
2. Щелкните **Перезагрузить**, чтобы перезагрузить Azure Data Studio и увидеть книгу Jupyter. Щелкните **Открыть новый экземпляр**, чтобы открыть новый экземпляр Azure Data Studio с книгой Jupyter.
3. В окне проводника должен быть раздел **Книги**. Если он не развернут, щелкните его, чтобы просмотреть записные книжки.
4. Щелкните записную книжку, соответствующую нужной задаче.

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о записных книжках в Azure Data Studio см. в статье [Использование записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

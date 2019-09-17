---
title: Управление кластером больших данных SQL Server с помощью записных книжек Azure Data Studio
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Используйте записную книжку из Azure Data Studio для управления кластером больших данных и устранения его неполадок.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cb2fcaf7431b5d79698af009b533ee49254777fe
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70846647"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Управление кластерами больших данных SQL Server с помощью записных книжек Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет расширение для Azure Data Studio, включающее в себя записные книжки. Записная книжка содержит документацию и код, которые можно использовать в Azure Data Studio для управления кластерами больших данных SQL Server.

[Записные книжки](notebooks-guidance.md), которые изначально были реализованы как проект с открытым кодом, теперь интегрированы в [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download). Вы можете использовать разметку Markdown для текста в текстовых ячейках и одно из доступных ядер для написания кода в ячейках кода.

С помощью записных книжках можно развертывать кластеры больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Помимо записных книжек, пользователи могут просматривать набор записных книжек, которые называются книгами Jupyter. Книга Jupyter содержит оглавление для навигации по коллекции записных книжек, что позволяет пользователю легко найти требуемую записную книжку для устранения неполадок SQL Server или просмотра состояния кластера.

## <a name="prerequisites"></a>Предварительные требования

Для запуска записной книжки требуются следующие компоненты:

* последняя [сборка Azure Data Studio для участников программы предварительной оценки](https://aka.ms/azuredatastudio-rc);
* расширение [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], установленное в Azure Data Studio.

Помимо перечисленных выше компонентов, для развертывания кластера больших данных SQL Server 2019 требуется следующее:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>Доступ к записным книжкам для устранения неполадок
Существует три способа доступа к записным книжкам для устранения неполадок.

### <a name="command-palette"></a>Палитра команд
1. Щелкните **Просмотр** , а затем **Палитра команд**
2. Введите Jupyter Books: SQL Server Guide 2019 "
3. При этом будут открыты книги Jupyter проводника с книгой Jupyter, содержащей ТСГ, связанный с SQL Server кластерами больших данных.

### <a name="sql-master-dashboard"></a>Главная панель мониторинга SQL
1. После установки Azure Data Studio для участников программы предварительной оценки подключитесь к экземпляру кластера больших данных SQL Server.
2. После успешного подключения щелкните правой кнопкой мыши имя сервера в мини-приложении "Подключения" и выберите пункт **Управление**.
3. На панели мониторинга щелкните **Кластер больших данных SQL Server**. Щелкните **руководство по SQL Server 2019**, чтобы открыть книгу Jupyter с нужными записными книжками.
    ![кнопка](media/manage-notebooks/jupyter-book-button.png)

1. Откроется книга Jupyter проводника с уже открытой книгой ТСГ Jupyter.
4. Щелкните записную книжку, соответствующую нужной задаче.

### <a name="controller-dashboard"></a>Панель мониторинга контроллера
1. В представлении **подключения** разверните узел **SQL Server кластеры больших данных.**
2. Добавьте сведения о конечной точке контроллера.
3. После успешного подключения к контроллеру щелкните правой кнопкой мыши конечную точку и выберите пункт **Управление.**
4. После загрузки панели мониторинга нажмите кнопку Устранение неполадок, чтобы запустить книгу Jupyter ТСГ.

## <a name="how-to-use-troubleshooting-notebooks"></a>Как использовать устранение неполадок в записных книжках
1. Просмотрите оглавление существующей книги Jupyter, пока не найдете нужные ТСГ.
1. Все записные книжки оптимизированы, когда пользователю нужно щелкнуть только **ячейки Run.** Каждая ячейка в записной книжке будет запускаться по отдельности, пока она не будет завершена.
1. При возникновении ошибки в книге Jupyter предлагается Записная книжка, которую можно запустить для устранения этой ошибки. Выполните действия, а затем повторно запустите записную книжку.

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о записных книжках в Azure Data Studio см. в статье [Использование записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

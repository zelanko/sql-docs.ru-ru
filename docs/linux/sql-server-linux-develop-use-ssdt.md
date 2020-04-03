---
title: Разработка и развертывание баз данных SQL Server для Linux  | Документация Майкрософт
description: Набор средств SQL Server Data Tools с Visual Studio — это эффективная среда разработки и управления жизненным циклом баз данных для SQL Server на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.openlocfilehash: 50f6e9a2b3292cb94f335092ef590ba6fb9ea422
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80216820"
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Создание баз данных для SQL Server на Linux с помощью Visual Studio

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Набор средств SQL Server Data Tools (SSDT) превращает Visual Studio в эффективную среду разработки и управления жизненным циклом баз данных (DLM) для SQL Server на Linux. Вы можете спроектировать, собрать, протестировать и опубликовать базу данных из проекта, находящегося в системе управления версиями, точно так же, как и при разработке кода приложения.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Установка Visual Studio и SQL Server Data Tools

1. Если вы еще не установили Visual Studio на компьютере c Windows, [скачайте и установите Visual Studio](https://visualstudio.microsoft.com/downloads/). Если у вас нет лицензии Visual Studio, используйте выпуск Visual Studio Community — бесплатную полнофункциональную интегрированную среду разработки для учащихся, проектов с открытым исходным кодом и индивидуальных разработчиков.

2. Во время установки Visual Studio выберите **Выборочная** для параметра **Выберите тип установки**. Нажмите кнопку **Далее**

3. Выберите **Microsoft SQL Server Data Tools**, **Git для Windows** и **Расширение GitHub для Visual Studio** в списке выбора функций.

   <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Продолжите и завершите установку Visual Studio. Это может занять несколько минут.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>Обновление SQL Server Data Tools до выпуска SSDT 17.0 RC

SQL Server на Linux поддерживается SSDT 17.0 RC или более поздней версии.

* [Скачайте и установите SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939).

## <a name="create-a-new-database-project-in-source-control"></a>Создание проекта базы данных в системе управления версиями

1. Запустите Visual Studio.

2. Выберите **Team Explorer** в меню **Вид**. 

3. Щелкните **Создать** в разделе **Локальный репозиторий Git** страницы **Подключение**.

   <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

4. Нажмите кнопку **Создать**. После создания локального репозитория Git дважды щелкните **SSDTRepo**.

5. Щелкните **Создать** в разделе **Решения**. Выберите **SQL Server** в узле **Другие языки** диалогового окна **Создание проекта**.

   <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

6. Введите **TutorialDB** в качестве имени и нажмите кнопку **ОК**, чтобы создать проект базы данных.

## <a name="create-a-new-table-in-the-database-project"></a>Создание таблицы в проекте базы данных

1. Выберите **Обозреватель решений** в меню **Вид**.

2. Откройте меню проекта базы данных, щелкнув правой кнопкой мыши **TutorialDB** в обозревателе решений.

3. Выберите **Таблица** в области **Добавить**.

   <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. С помощью конструктора таблиц добавьте два столбца — "Имя" `nvarchar(50)` и "Расположение" `nvarchar(50)`, как показано на рисунке. SSDT создает скрипт `CREATE TABLE` при добавлении столбцов в конструкторе.

   <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Сохраните файл **Table1.sql**.

## <a name="build-and-validate-the-database"></a>Сборка и проверка базы данных

1. Откройте меню проекта базы данных для **TutorialDB** и выберите **Сборка**. SSDT компилирует SQL-файлы исходного кода в проекте и создает файл пакета приложения уровня данных (DACPAC). Это можно использовать для публикации базы данных в экземпляре SQL Server на Linux. 

   <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Проверьте сообщение об успешном завершении сборки в окне **Вывод** в Visual Studio. 

## <a name="publish-the-database-to-sql-server-instance-on-linux"></a>Публикация базы данных в экземпляре SQL Server на Linux.

1. Откройте меню проекта базы данных для **TutorialDB** и выберите **Опубликовать**.

2. Щелкните **Изменить**, чтобы выбрать экземпляр SQL Server на Linux.

   <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. В диалоговом окне подключения введите IP-адрес или имя узла своего экземпляра SQL Server в Linux, имя пользователя и пароль.

   <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Нажмите кнопку **Опубликовать** в диалоговом окне публикации.

5. Проверьте состояние публикации в окне **Операции инструментальных средств для обработки данных**.

6. Щелкните **Просмотреть результаты** или **Просмотреть скрипт**, чтобы просмотреть сведения о результатах публикации базы данных в SQL Server на Linux.

   <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Вы успешно создали базу данных в экземпляре SQL Server на Linux и познакомились с основами разработки базы данных с помощью проекта базы данных, находящегося в системе управления версиями.

## <a name="next-steps"></a>Дальнейшие действия

Если вы не знакомы с T-SQL, изучите статьи [Руководство. Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md).

Дополнительные сведения о разработке базы данных с помощью SQL Data Tools см. в представленных ниже статьях.

* [Скачивание и установка Visual Studio](https://www.visualstudio.com/downloads/)
* [Скачивание и установка SSDT](https://aka.ms/ssdt-download)
* [Документация MSDN по SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)
* [Руководство. Составление инструкций Transact-SQL](https://msdn.microsoft.com/library/ms365303.aspx)
* [Справочник по Transact-SQL (ядро СУБД)](https://msdn.microsoft.com/library/bb510741.aspx)

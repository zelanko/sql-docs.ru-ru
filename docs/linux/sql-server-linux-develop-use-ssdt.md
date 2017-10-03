---
title: "Разработка и развертывание SQL Server databases для Linux | Документы Microsoft"
description: 
author: erickangMSFT
ms.author: erickang
manager: jroth
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 9a639559de35573c7fb6dfdcc98c9d9680312659
ms.contentlocale: ru-ru
ms.lasthandoff: 10/02/2017

---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Используйте Visual Studio для создания баз данных для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server Data Tools (SSDT) примет мощные среды разработки и база данных жизненного цикла управление Жизненным Visual Studio для SQL Server в Linux. Можно разрабатывать, создания, тестирования и публикации базы данных из проекта системы управления версиями, так же, как разрабатывать код вашего приложения.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Установите Visual Studio и SQL Server Data Tools

1. Если вы еще не установили Visual Studio на компьютере Windows [загрузки и установки Visual Studio]. Если нет лицензии Visual Studio, Visual Studio Community edition является бесплатной, полнофункциональной интегрированной среды разработки для учащихся, открытым исходным кодом и для отдельных разработчиков.

2. Во время установки Visual Studio, выберите **настраиваемый** для **выберите тип установки** параметр. Нажмите кнопку **Далее**

3. Выберите **Microsoft SQL Server Data Tools**, **Git для Windows**, и **расширение GitHub для Visual Studio** из списка выбора компонентов.

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Продолжить и завершите установку Visual Studio. Может занять несколько минут.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>Обновление SQL Server Data Tools до выпуска версии-Кандидата 17.0 SSDT

2017 г. SQL Server в Linux поддерживает SSDT 17.0 версии-КАНДИДАТА или более поздней версии.

* [Загрузите и установите SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939).

## <a name="create-a-new-database-project-in-source-control"></a>Создайте новый проект базы данных в системе управления версиями

1. Запустите Visual Studio.

2. Выберите **Team Explorer** на **представление** меню. 

3. Нажмите кнопку **New** в **локального репозитория Git** статьи на **Connect** страницы.

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. Нажмите кнопку **Создать**. После создания локального репозитория Git, дважды щелкните **SSDTRepo**.

4. Нажмите кнопку **New** в **решения** раздела. Выберите **SQL Server** под **другие языки** узел в **новый проект** диалогового окна.

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. Введите в **TutorialDB** имя и нажмите кнопку **ОК** для создания нового проекта базы данных.

## <a name="create-a-new-table-in-the-database-project"></a>Создать новую таблицу в проект базы данных

1. Выберите **обозревателе решений** на **представление** меню.

2. Откройте меню Проект базы данных, щелкнув правой кнопкой мыши **TutorialDB** в обозревателе решений.

3. Выберите **таблицы** под **добавить**.

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. С помощью конструктора таблиц, добавления двух столбцов, имя `nvarchar(50)` и расположение `nvarchar(50)`, как показано на рисунке. SSDT приводит к возникновению ошибки `CREATE TABLE` скрипт по мере добавления столбцов в конструкторе.

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Сохранить **Table1.sql** файла.

## <a name="build-and-validate-the-database"></a>Построение и проверка базы данных

1. Откройте меню Проект базы данных на **TutorialDB** и выберите **сборки**. SSDT .sql файлов исходного кода в проекте и создает файл пакета (dacpac) приложения уровня данных. Это можно использовать для публикации базы данных к экземпляру 2017 г. SQL Server в Linux. 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Проверьте сообщение об успешном выполнении сборки **выходной** в Visual Studio. 

## <a name="publish-the-database-to-sql-server-2017-instance-on-linux"></a>Опубликовать базу данных к экземпляру 2017 г. SQL Server в Linux

1. Откройте меню Проект базы данных на **TutorialDB** и выберите **публикации**.

2. Нажмите кнопку **изменить** чтобы выбрать экземпляр SQL Server в Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. В диалоговом окне соединения введите IP-адрес или имя экземпляра SQL Server в Linux, имя пользователя и пароль.

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Нажмите кнопку **публикации** кнопку в диалоговом окне публикации.

5. Проверьте состояние публикации **операции Data Tools** окна.

6. Нажмите кнопку **Reulst представление** или **просмотреть сценарий** для получения подробных сведений о databsae публикации результат на сервере SQL Server в Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Успешно создана новая база данных на экземпляре SQL Server в Linux и знакомства с основами разработки базы данных с проектом базы данных системы управления версиями.

## <a name="next-steps"></a>Следующие шаги

Если вы не знакомы с T-SQL, см. раздел [учебника: написание инструкций Transact-SQL] и [Справочник по Transact-SQL (компонент Database Engine)].

Дополнительные сведения о разработке базы данных с SQL Data Tools см. в разделе [документы MSDN по SSDT]

[загрузки и установки Visual Studio]:https://www.visualstudio.com/downloads/
[Download and Install SSDT 17.0 RC2]:https://aka.ms/ssdt-download
[документы MSDN по SSDT]: https://msdn.microsoft.com/en-us/library/hh272686(v=vs.103).aspx
[учебника: написание инструкций Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[Справочник по Transact-SQL (компонент Database Engine)]:https://msdn.microsoft.com/library/bb510741.aspx

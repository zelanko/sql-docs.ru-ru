---
title: Разработка и развертывание SQL Server, базы данных для Linux | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.openlocfilehash: fafec68510e2c9214ed77294314b2ff06e456ff2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713286"
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Использовать Visual Studio для создания баз данных для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Data Tools (SSDT) превращает Visual Studio в это мощная среда разработки и базы данных жизненного цикла management (DLM) для SQL Server в Linux. Можно разрабатывать, создания, тестирования и публикации базы данных из проекта, контролируемого системой управления версиями, так же, как разрабатывать код приложения.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Установка Visual Studio и SQL Server Data Tools

1. Если вы еще не установили Visual Studio на компьютере Windows, [Скачайте и установите Visual Studio]. Если у вас нет лицензии на Visual Studio, Visual Studio Community edition — это бесплатная полнофункциональная интегрированная среда разработки для учащихся, разработчиков открытого по и отдельных.

2. Во время установки Visual Studio, выберите **Custom** для **выберите тип установки** параметр. Нажмите кнопку **Далее**

3. Выберите **Microsoft SQL Server Data Tools**, **Git для Windows**, и **расширение GitHub для Visual Studio** из списка выбора компонентов.

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Продолжить и завершите установку Visual Studio. Может занять несколько минут.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>Обновление SQL Server Data Tools до выпуска версии-Кандидата SSDT 17.0

SQL Server в Linux поддерживается SSDT 17.0, версия-КАНДИДАТ или более поздней версии.

* [Скачать и установить SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939).

## <a name="create-a-new-database-project-in-source-control"></a>Создайте новый проект базы данных в системе управления версиями

1. Запустите Visual Studio.

2. Выберите **Team Explorer** на **представление** меню. 

3. Нажмите кнопку **New** в **локального репозитория Git** разделе **Connect** страницы.

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. Нажмите кнопку **Создать**. После создания локального репозитория Git, дважды щелкните **SSDTRepo**.

4. Нажмите кнопку **New** в **решения** раздел. Выберите **SQL Server** под **другие языки** узел в **новый проект** диалоговое окно.

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. Введите в **TutorialDB** имя и нажмите кнопку **ОК** для создания нового проекта базы данных.

## <a name="create-a-new-table-in-the-database-project"></a>Создать новую таблицу в проект базы данных

1. Выберите **обозревателе решений** на **представление** меню.

2. Откройте меню "проект базы данных", щелкнув правой кнопкой мыши **TutorialDB** в обозревателе решений.

3. Выберите **таблицы** под **добавить**.

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. С помощью конструктора таблиц, добавьте два столбца, имя `nvarchar(50)` и расположение `nvarchar(50)`, как показано на рисунке. Создает SSDT `CREATE TABLE` скрипт по мере добавления столбцов в конструкторе.

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Сохранить **Table1.sql** файла.

## <a name="build-and-validate-the-database"></a>Создание и проверка базы данных

1. Откройте меню "проект базы данных" на **TutorialDB** и выберите **построения**. SSDT компиляция файлов исходного кода .sql в проекте и создает файл пакета (dacpac) приложения уровня данных. Это можно публиковать базу данных к экземпляру SQL Server в Linux. 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Проверьте сообщение об успешном выполнении сборки **вывода** окно в Visual Studio. 

## <a name="publish-the-database-to-sql-server-instance-on-linux"></a>Опубликовать базу данных к экземпляру SQL Server в Linux

1. Откройте меню "проект базы данных" на **TutorialDB** и выберите **публикации**.

2. Нажмите кнопку **изменить** чтобы выбрать экземпляр SQL Server в Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. В диалоговом окне соединения введите IP-адрес или имя экземпляра SQL Server в Linux, имя пользователя и пароль.

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Нажмите кнопку **публикации** кнопку в диалоговом окне публикации.

5. Проверить состояние публикации **операции Data Tools** окна.

6. Нажмите кнопку **Просмотр результатов** или **просмотреть сценарий** для просмотра сведений базы данных публикации результат в SQL Server в Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Вы успешно создать новую базу данных на экземпляре SQL Server в Linux и ознакомились с основами разработки базы данных с проектом базы данных, контролируемых системой управления версиями.

## <a name="next-steps"></a>Следующие шаги

Если вы не знакомы с T-SQL, см. в разделе [Учебник. Составление инструкций Transact-SQL] и [Справочник по Transact-SQL (ядро СУБД)].

Дополнительные сведения о разработке базы данных с помощью SQL Data Tools, см. в разделе [документы MSDN по SSDT]

[Скачайте и установите Visual Studio]: https://www.visualstudio.com/downloads/
[Download and Install SSDT]:https://aka.ms/ssdt-download
[Документы MSDN по SSDT]: https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx
[Учебник. Составление инструкций Transact-SQL]: https://msdn.microsoft.com/library/ms365303.aspx
[Справочник по Transact-SQL (ядро СУБД)]: https://msdn.microsoft.com/library/bb510741.aspx

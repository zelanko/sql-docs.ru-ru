---
title: "Приступая к работе с простой пример мастера импорта и экспорта | Документы Microsoft"
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: ea3db39b-698b-4a74-8eb8-21dc7252dc1a
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 9eee58be471d8b39b051c1343f9eb26a2960b6d6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="get-started-with-this-simple-example-of-the-import-and-export-wizard"></a>Приступая к работе с простой пример мастера импорта и экспорта
Узнайте, что следует ожидать в мастере экспорта и импорта SQL Server при рассмотрении типичный сценарий — Импорт данных из электронной таблицы Excel к базе данных SQL Server. Даже если вы планируете использовать другой источник и назначение другой, в этом разделе показано большинство что нужно знать о запуске мастера.

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Необходимое условие - — это мастер, установленной на компьютере?
Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="heres-the-excel-source-data-for-this-example"></a>Ниже приведен в этом примере источник данных Excel
Вот исходные данные, которые вы собираетесь скопировать - небольшая таблица двух столбцов на листе WizardWalkthrough книги WizardWalkthrough.xlsx Excel.

![Источник данных Excel](../../integration-services/import-export-data/media/excel-source-data.jpg)

## <a name="heres-the-sql-server-destination-database-for-this-example"></a>Вот целевой базе данных SQL Server для этого примера
(В SQL Server Management Studio) вот целевой базы данных SQL Server, к которому вы собираетесь скопировать исходные данные. В целевой таблице не существует - вы собираетесь разрешить мастеру создать таблицу для вас.

![Целевая база данных SQL Server](../../integration-services/import-export-data/media/sql-server-destination-database.jpg)

## <a name="step-1---start-the-wizard"></a>Шаг 1. запуск мастера
Запустите мастер из группы Microsoft SQL Server 2016, в меню «Пуск».

![Запуск мастера](../../integration-services/import-export-data/media/start-wizard.jpg)

> [!NOTE]
> Для этого примера выберите 32-разрядный мастер из-за наличия 32-разрядной версии Microsoft Office установлен. Поэтому необходимо использовать 32-разрядный поставщик для подключения к Excel. Для многих других источников данных обычно можно выбрать 64-разрядный мастер.
>
> Чтобы использовать 64-разрядной версии мастера экспорта и импорта SQL Server, необходимо установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS), 32-разрядных приложений и установить только 32-разрядных файлов, включая 32-разрядную версию мастера.

Дополнительные сведения см. в разделе [Запуск мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

## <a name="step-2---view-the-welcome-page"></a>Шаг 2 - Просмотр страницы приветствия
Первая страница мастера **приветствия** страницы. 

Возможно, не нужно просмотреть эту страницу еще раз, поэтому действуйте и нажмите кнопку **больше не показывать это окно**.

![Добро пожаловать в мастер](../../integration-services/import-export-data/media/welcome-to-the-wizard.jpg)

## <a name="step-3---pick-excel-as-your-data-source"></a>Шаг 3. выбора Excel в качестве источника данных
На следующей странице **выберите источник данных**, выбрать Microsoft Excel в качестве источника данных. Перейдите к выберите файл Excel. Наконец, вы укажите версию Excel, которая использовалась для создания файла.

![Выберите источник данных Excel](../../integration-services/import-export-data/media/choose-the-excel-data-source.jpg)

Дополнительные сведения о подключении к Excel см. в разделе [соединение с источником данных Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md). Дополнительные сведения об этой странице мастера см. в разделе [выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md).

## <a name="step-4---pick-sql-server-as-your-destination"></a>Шаг 4. выбора SQL Server в качестве места расположения
На следующей странице **Выбор назначения**, как к назначению путем выбора одного из поставщиков данных в списке, подключается к SQL Server, выберите Microsoft SQL Server. В этом примере выберите **.Net Framework поставщик данных для SQL Server**.

Страница отображает список свойств поставщика. Многие из них являются чужим имена и неизвестные параметры. К счастью Чтобы подключиться к любую базу данных, обычно необходимо предоставить только следующие данные. Можно игнорировать значения по умолчанию для других параметров.

|Необходимые сведения|.NET framework поставщика данных для свойства SQL Server|
|---|---|
|Имя сервера|**Источник данных**|
|Сведения о проверке подлинности (имя входа)|**Встроенная безопасность**; или **идентификатор пользователя** и **пароль**<br/>Если вы хотите просмотреть список раскрывающегося списка баз данных на сервере, сначала необходимо ввести допустимое имя входа сведения.|
|Имя базы данных|**Исходный каталог**|

![Выберите место назначения SQL Server](../../integration-services/import-export-data/media/choose-the-sql-server-destination.jpg)

Дополнительные сведения о подключении к SQL Server см. в разделе [подключение к источнику данных SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md). Дополнительные сведения об этой странице мастера см. в разделе [Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).

## <a name="step-5---copy-a-table-instead-of-writing-a-query"></a>Шаг 5 – копирование таблицы вместо написания запроса
На следующей странице **Выбор копирования таблицы или запроса**, укажите, требуется скопировать всю таблицу исходных данных. Не следует создавать запросы на языке SQL, чтобы выбрать данные для копирования.

![Укажите для копирования таблицы](../../integration-services/import-export-data/media/specify-to-copy-a-table.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Выбор копирования таблицы или запроса](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).

## <a name="step-6---pick-the-table-to-copy"></a>Шаг 6 - выбрать таблицы для копирования
На следующей странице **Выбор исходных таблиц и представлений**, выберите таблицу или таблицы, которые необходимо копировать из источника данных. Затем сопоставить каждой выбранной исходной таблицы в новую или существующую целевую таблицу.

В этом примере по умолчанию мастер назначил **WizardWalkthrough$** лист в **источника** столбца в новую таблицу с тем же именем на целевом сервере SQL Server. (Книга Excel содержит только один рабочий лист.)
-   Знак доллара ($) на имя исходной таблицы указывает на листе Excel. (Именованный циклы в Excel представляется только по своему имени.)
-   Звезда на значок таблицы назначения указывает, что мастер будет создана новая целевая таблица.

![Выберите таблицу (до переименования)](../../integration-services/import-export-data/media/select-the-table-before-renaming.jpg)

Может потребоваться удалить знак доллара ($) от имени новой целевой таблицы.

![Выберите таблицу (после переименования)](../../integration-services/import-export-data/media/select-the-table-after-renaming.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Выбор исходных таблиц и представлений](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md).

## <a name="optional-step-7---review-the-column-mappings"></a>Необязательный шаг 7. Проверьте сопоставления столбцов
Перед выходом **Выбор исходных таблиц и представлений** при необходимости щелкните **изменить сопоставления** кнопку, чтобы открыть **сопоставления столбцов** диалоговое окно. Здесь в **сопоставления** таблицы, вы видите, как мастер будет сопоставляются со столбцами в таблице назначения новых столбцов в исходном листе.

![Просмотр сопоставлений столбцов](../../integration-services/import-export-data/media/view-column-mappings.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [сопоставления столбцов](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).

## <a name="optional-step-8---review-the-create-table-statement"></a>Необязательный шаг 8. Проверьте инструкцию CREATE TABLE
Хотя **сопоставления столбцов** открыто диалоговое окно, можно нажать кнопку **изменить SQL** кнопку, чтобы открыть **инструкция SQL Create Table** диалоговое окно. Вы увидите **CREATE TABLE** инструкции, созданные с помощью мастера для создания новой целевой таблицы. Обычно не нужно изменять инструкцию.

![Инструкции CREATE TABLE, представление](../../integration-services/import-export-data/media/view-create-table-statement.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [инструкция SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).

## <a name="optional-step-9---preview-the-data-to-copy"></a>Необязательный шаг 9. Просмотр данных для копирования
После нажатия кнопки **ОК** закрыть **инструкция SQL Create Table** диалогового окна, а затем нажмите кнопку **ОК** , чтобы закрыть **сопоставления столбцов** диалоговое окно, вы снова **Выбор исходных таблиц и представлений** страницы. При необходимости щелкните **предварительного просмотра** кнопку, чтобы просмотреть образец данных, мастер происходит копирование. В этом примере он правилен.

![Просмотр данных для копирования](../../integration-services/import-export-data/media/preview-data-to-copy.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [данные для предварительного просмотра](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).

## <a name="step-10---yes-you-want-to-run-the-import-export-operation"></a>Шаг 10 — Да, вы хотите запустить операцию импорта экспорта
На следующей странице **сохранить и запустить пакет**, оставить **немедленно запустить** включена для копирования данных, как вы нажмете **Готово** на следующей странице. Или следующую страницу можно пропустить, нажав кнопку **Готово** на **сохранить и запустить пакет** страницы.

![Выполнение пакета](../../integration-services/import-export-data/media/run-the-package.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [сохранить и запустить пакет](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).

## <a name="step-11---finish-the-wizard-and-run-the-import-export-operation"></a>Шаг 11 — завершить работу мастера и выполнить операцию импорта экспорта
Если вы нажали кнопку **Далее** вместо **Готово** на **сохранить и запустить пакет** нажмите на следующую страницу страницы **завершения работы мастера**, просматривать сводки мастера, которая должна выполнять. Нажмите кнопку **Готово** для запуска операции импорта экспорта.

![Завершение работы мастера](../../integration-services/import-export-data/media/complete-the-wizard.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [завершения работы мастера](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).

## <a name="step-12---review-what-the-wizard-did"></a>Шаг 12 - просмотрите Мастер выполнил
На последней странице следите за каждой задачи завершения работы мастера, а затем просмотрите результаты. Выделенная строка указывает, что мастер успешно скопировать данные. По завершении вы сможете!

![Мастер успешно](../../integration-services/import-export-data/media/the-wizard-succeeded.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [выполнение операции](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md).

## <a name="heres-the-new-table-of-data-copied-to-sql-server"></a>Вот новую таблицу данных, копируемых в SQL Server
(В SQL Server Management Studio) вы увидите новый целевой таблицы, мастер создал в SQL Server.

![Данные, копируемые в SQL Server](../../integration-services/import-export-data/media/data-copied-to-sql-server.jpg)

(В SSMS) вы увидите данные, мастер копируемых в SQL Server.

![Данных, копируемых в SQL Server 2](../../integration-services/import-export-data/media/data-copied-to-sql-server-2.jpg)

## <a name="learn-more"></a>Дополнительные сведения  
Дополнительные сведения о работе мастера.
-   **Дополнительные сведения о мастере.** Обзор мастера см. в статье [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

-   **Дополнительные сведения о шагах в мастере.** Если вы ищете сведения о шагах в мастере, выберите нужную страницу из списка- [шаги в мастере экспорта и импорта SQL Server](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Имеется также отдельной странице документации для каждой страницы мастера.

-   **Сведения о подключении к источникам данных и назначения.** Если вы ищете сведения о подключении к данным, выберите нужную страницу из списка- [подключение к источникам данных с помощью мастера экспорта и импорта SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Нет отдельной странице документации для каждой из нескольких источников часто используемых данных.




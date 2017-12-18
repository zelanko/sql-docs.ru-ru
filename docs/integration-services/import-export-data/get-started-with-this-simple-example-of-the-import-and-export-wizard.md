---
title: "Приступая к работе с простым примером мастера импорта и экспорта | Документы Майкрософт"
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: ea3db39b-698b-4a74-8eb8-21dc7252dc1a
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 523dcd99da61b11e42848ea77037baf59a3ea00b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="get-started-with-this-simple-example-of-the-import-and-export-wizard"></a>Приступая к работе с простым примером мастера импорта и экспорта
Сведения о том, что следует ожидать от мастера экспорта и импорта SQL Server, на примере типичного сценария — импорта данных из электронной таблицы Excel в базу данных SQL Server. Даже если вы планируете использовать другой источник и другое назначение, в этом разделе вы найдете основную часть сведений о работе с мастером.

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Предварительное требование — у вас на компьютере установлен этот мастер?
Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="heres-the-excel-source-data-for-this-example"></a>Исходные данные для этого примера Excel
Это исходные данные, которые вы собираетесь скопировать, — небольшая таблица из двух столбцов на листе WizardWalkthrough в книге WizardWalkthrough.xlsx Excel.

![Исходные данные Excel](../../integration-services/import-export-data/media/excel-source-data.jpg)

## <a name="heres-the-sql-server-destination-database-for-this-example"></a>Целевая база данных SQL Server для этого примера
Это целевая база данных SQL Server (в SQL Server Management Studio), куда вы собираетесь скопировать исходные данные. Целевая таблица не существует, поэтому вы позволите мастеру создать ее для вас.

![Целевая база данных SQL Server](../../integration-services/import-export-data/media/sql-server-destination-database.jpg)

## <a name="step-1---start-the-wizard"></a>Шаг 1. Запуск мастера
Запустите мастер из группы "Microsoft SQL Server 2016" в меню "Пуск" Windows.

![Запуск мастера](../../integration-services/import-export-data/media/start-wizard.jpg)

> [!NOTE]
> Для этого примера выберите 32-разрядный мастер, так как у вас установлена 32-разрядная версия Microsoft Office. Поэтому нужно использовать 32-разрядный поставщик данных для подключения к Excel. Для многих других источников данных в большинстве случаев можно выбрать 64-разрядный мастер.
>
> Чтобы использовать 64-разрядную версию мастера экспорта и импорта SQL Server, нужно установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS) являются 32-разрядными приложениями и устанавливают только 32-разрядные файлы, включая 32-разрядную версию мастера.

Дополнительные сведения см. в разделе [Запуск мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

## <a name="step-2---view-the-welcome-page"></a>Шаг 2. Просмотр страницы приветствия
Первая страница мастера — это страница **приветствия**. 

Если вы не хотите, чтобы она открывалась снова, установите флажок **Больше не показывать это окно**.

![Вас приветствует мастер](../../integration-services/import-export-data/media/welcome-to-the-wizard.jpg)

## <a name="step-3---pick-excel-as-your-data-source"></a>Шаг 3. Выбор Excel в качестве источника данных
На следующей странице **Выбор источника данных** выберите Microsoft Excel в качестве источника данных. Затем перейдите к файлу Excel и выберите его. Наконец, укажите версию Excel, которую вы использовали для создания файла.

![Выбор источника данных Excel](../../integration-services/import-export-data/media/choose-the-excel-data-source.jpg)

Дополнительные сведения о подключении к Excel см. в разделе [Подключение к источнику данных Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md). Дополнительные сведения об этой странице мастера см. в разделе [Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md).

## <a name="step-4---pick-sql-server-as-your-destination"></a>Шаг 4. Выбор SQL Server в качестве назначения
На следующей странице **Выбор назначения** выберите Microsoft SQL Server в качестве назначения, выбрав в списке одного из поставщиков данных, подключающегося к SQL Server. В этом примере выберите **Поставщик данных .Net Framework для SQL Server**.

На странице отображается список свойств поставщика. Многие из них могут быть вам незнакомы или иметь непонятные имена. К счастью, для подключения к любой корпоративной базе данных, как правило, достаточно указать лишь три параметра. Остальные параметры можно пропустить.

|Необходимые сведения|Свойство "Поставщик данных .NET Framework для SQL Server"|
|---|---|
|Имя сервера|**Источник данных**|
|Сведения для проверки подлинности (имя входа)|**Встроенная система безопасности** или **Идентификатор пользователя** и **Пароль**<br/>Чтобы открыть раскрывающийся список баз данных на сервере, сначала нужно указать действительные данные для входа.|
|Имя базы данных|**Исходный каталог**|

![Выбор назначения SQL Server](../../integration-services/import-export-data/media/choose-the-sql-server-destination.jpg)

Дополнительные сведения о подключении к SQL Server см. в разделе [Подключение к источнику данных SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md). Дополнительные сведения об этой странице мастера см. в разделе [Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).

## <a name="step-5---copy-a-table-instead-of-writing-a-query"></a>Шаг 5. Копирование таблицы вместо написания запроса
На следующей странице **Выбор копирования таблицы или запроса** укажите, что нужно скопировать всю таблицу исходных данных. Вам не нужно создавать запрос на языке SQL, чтобы выбрать данные для копирования.

![Указание копирования таблицы](../../integration-services/import-export-data/media/specify-to-copy-a-table.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Выбор копирования таблицы или запроса](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).

## <a name="step-6---pick-the-table-to-copy"></a>Шаг 6. Выбор копируемой таблицы
На следующей странице **Выбор исходных таблиц и представлений** выберите таблицу или таблицы, которые необходимо копировать из источника данных. Затем следует сопоставить каждую из выбранных исходных таблиц с новой или существующей целевой таблицей.

В этом примере по умолчанию мастер сопоставил лист **WizardWalkthrough$** в столбце **Source** с новой таблицей с таким же именем в назначении SQL Server. (Книга Excel содержит всего один рабочий лист.)
-   Знак доллара ($) на имени исходной таблицы обозначает лист Excel. (Именованный диапазон в Excel представлен лишь своим именем.)
-   Звезда на значке целевой таблицы указывает, что мастер создаст новую целевую таблицу.

![Выбор таблицы (перед переименованием)](../../integration-services/import-export-data/media/select-the-table-before-renaming.jpg)

Может потребоваться удалить знак доллара ($) из имени новой целевой таблицы.

![Выбор таблицы (после переименования)](../../integration-services/import-export-data/media/select-the-table-after-renaming.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Выбор исходных таблиц и представлений](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md).

## <a name="optional-step-7---review-the-column-mappings"></a>Необязательный шаг 7. Проверка сопоставлений столбцов
Прежде чем закрыть страницу **Выбор исходных таблиц и представлений**, вы можете нажать кнопку **Изменить сопоставления**, чтобы открыть диалоговое окно **Сопоставления столбцов**. Здесь в таблице **Сопоставления** видно, как мастер будет сопоставлять столбцы на исходном листе со столбцами в целевой таблице.

![Просмотр сопоставлений столбцов](../../integration-services/import-export-data/media/view-column-mappings.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Сопоставления столбцов](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).

## <a name="optional-step-8---review-the-create-table-statement"></a>Необязательный шаг 8. Просмотр инструкции CREATE TABLE
Хотя диалоговое окно **Сопоставления столбцов** открыто, вы можете нажать кнопку **Изменить SQL**, чтобы открыть диалоговое окно **Инструкция SQL Create Table**. Вы увидите инструкцию **CREATE TABLE**, созданную мастером для создания целевой таблицы. Обычно менять эту инструкцию не требуется.

![Просмотр инструкции CREATE TABLE](../../integration-services/import-export-data/media/view-create-table-statement.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Инструкция SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).

## <a name="optional-step-9---preview-the-data-to-copy"></a>Необязательный шаг 9. Просмотр данных для копирования
Нажав кнопку **ОК** для закрытия диалогового окна **Инструкция SQL Create Table** и кнопку **ОК** для закрытия диалогового окна **Сопоставления столбцов**, вы вернетесь на страницу **Выбор исходных таблиц и представлений**. При необходимости нажмите кнопку **Предварительного просмотра**, чтобы просмотреть образец данных, которые мастер собирается скопировать. В этом примере он выглядит правильно.

![Просмотр копируемых данных](../../integration-services/import-export-data/media/preview-data-to-copy.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Предварительный просмотр данных](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).

## <a name="step-10---yes-you-want-to-run-the-import-export-operation"></a>Шаг 10. Требуется запустить операцию импорта-экспорта
На следующей странице **Сохранение и запуск пакета** оставьте параметр **Запустить немедленно** включенным, чтоб скопировать данные сразу после нажатия кнопки **Готово** на следующей странице. Либо вы можете пропустить следующую страницу, нажав кнопку **Готово** на странице **Сохранение и запуск пакета**.

![Запуск пакета](../../integration-services/import-export-data/media/run-the-package.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Сохранение и запуск пакета](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).

## <a name="step-11---finish-the-wizard-and-run-the-import-export-operation"></a>Шаг 11. Завершение работы с мастером и запуск операции импорта-экспорта
Если вы нажали кнопку **Далее** вместо **Готово** на странице **Сохранение и запуск пакета**, то на следующей странице **Завершение работы мастера** выводится сводка о дальнейших действиях мастера. Нажмите кнопку **Готово**, чтобы запустить операцию импорта-экспорта.

![Завершение работы мастера](../../integration-services/import-export-data/media/complete-the-wizard.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Завершение работы мастера](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).

## <a name="step-12---review-what-the-wizard-did"></a>Шаг 12. Просмотр результатов работы мастера
На последней странице наблюдайте, как мастер выполняет каждую задачу, а затем просмотрите результаты. Выделенная строка указывает, что мастер успешно скопировал ваши данные. Готово!

![Мастер выполнен успешно](../../integration-services/import-export-data/media/the-wizard-succeeded.jpg)

Дополнительные сведения об этой странице мастера см. в разделе [Выполнение операции](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md).

## <a name="heres-the-new-table-of-data-copied-to-sql-server"></a>Новая таблица данных, скопированная в SQL Server
Здесь видна новая целевая таблица (В SQL Server Management Studio), созданная мастером в SQL Server.

![Данные, скопированные в SQL Server](../../integration-services/import-export-data/media/data-copied-to-sql-server.jpg)

Здесь (опять в SSMS) видны данные, которые мастер скопировал в SQL Server.

![Данные, скопированные в SQL Server 2](../../integration-services/import-export-data/media/data-copied-to-sql-server-2.jpg)

## <a name="learn-more"></a>Дополнительные сведения  
Дополнительные сведения о работе мастера.
-   **Дополнительные сведения о мастере.** Обзор мастера см. в статье [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

-   **Дополнительные сведения о шагах в мастере.** Если вам нужна информация о процедурах, выполняемых в мастере, выберите нужную страницу в списке в разделе [Шаги в мастере импорта и экспорта SQL Server](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Каждой странице мастера соответствует отдельная страница документации.

-   **Сведения о подключении к источникам данных и назначениям.** Сведения о подключении к данным см. на соответствующей странице, выбрав ее в списке в разделе [Подключение к источникам данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Для каждого распространенного источника данных имеется отдельная страница документации.



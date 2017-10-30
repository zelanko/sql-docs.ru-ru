---
title: "Шаги в мастере экспорта и импорта SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 816fb1bd-7bb9-450d-ad65-e4c2d02eaff8
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 22d1f4b78fadab6d7b6659104b54a564f11da308
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="steps-in-the-sql-server-import-and-export-wizard"></a>Шаги в мастере экспорта и импорта SQL Server
В этом разделе описана последовательность действий для импорта и экспорта данных с помощью мастера экспорта и импорта SQL Server. Он также содержит ссылки на отдельные страницы документации, которые описывают каждую страницу или диалогового окна, отображаемые в мастере.

В этом разделе описывается только **действия** в мастере. Если вам нужны для других целей, см. раздел [задач и содержимого, связанные с](#related).

## <a name="steps-for-importing-and-exporting-data"></a>Действия для импорта и экспорта данных  
 В следующей таблице перечислены действия по импорту и экспорта данных и приведены соответствующие страницы мастера. В зависимости от параметров, выбранных в мастере обычно не видите эти страницы.  

Для быстрого просмотра на нескольких экранах, см в сеансе типичные, взгляните на этот простой пример начала до конца на одной странице - [Приступая к работе с простой пример мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

|Шаг|Страницы мастера|  
|----------|------------------|  
|**Начальная страница документации**<br />На этой странице никакие действия не требуются.|[Вас приветствует мастер импорта и экспорта SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)|  
|**Выберите источник** данных.|[Выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)|  
|**Выберите назначение** для данных.|[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)|  
|**Настройка назначения**. (Дополнительные шаги)<br /><br /> Создание целевой базы данных.<br />Если вы копируете данные в текстовый файл, настройте дополнительные параметры.|[Создание базы данных](../../integration-services/import-export-data/create-database-sql-server-import-and-export-wizard.md)<br /><br />[Настройка назначения «неструктурированный файл»](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)|  
|**Укажите, требуется скопировать.**|[Выбор копирования таблицы или запроса](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)<br /><br />[Выбор исходных таблиц и представлений](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)<br /><br />[Определение исходного запроса](../../integration-services/import-export-data/provide-a-source-query-sql-server-import-and-export-wizard.md)|  
|**Настройте операцию копирования**. (Дополнительные шаги)<br /><br /> Создание целевой таблицы.<br />-Выбрать, что делать, если мастер не знает, как для сопоставления типов данных между источником и назначением выбранного.<br />Проверка сопоставлений столбцов между источником и назначением.<br />Решение проблем с преобразованием типов данных между источником и назначением.<br />Просмотр данных для копирования.|[Инструкция SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md)<br /><br />[Преобразование типов без проверки](../../integration-services/import-export-data/convert-types-without-conversion-checking-sql-server-import-and-export-wizard.md)<br /><br />[Сопоставления столбцов](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)<br /><br />[Просмотр сопоставления типов данных](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)<br /><br />[Диалоговое окно сведений преобразование столбца](../../integration-services/import-export-data/column-conversion-details-dialog-box-sql-server-import-and-export-wizard.md)<br /><br />[Диалоговое окно предварительного просмотра данных](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)|  
|**Скопируйте данные.**<br /><br /> При необходимости сохраните их в виде пакета SQL Server Integration Services (SSIS).|[Сохраните и выполните пакет](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)<br /><br />[Сохранить пакет служб SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)<br /><br />[Завершите работу мастера](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)<br /><br />[Выполнение операции](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md)|  

> [!TIP]
> Нажмите клавишу F1 при просмотре любой страницы или диалогового окна, чтобы открыть документацию по текущей странице мастера.

## <a name="related"></a>Связанные задачи и содержимое  
Ниже приведены некоторые основные задачи.
-   **См. краткий пример того, как работает мастер.**

    -   **Если вы хотите просмотреть снимков экрана.** Рассмотрим этот простой пример начала до конца на одной странице - [Приступая к работе с простой пример мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Если вы предпочитаете смотреть видео.** В этом видеоролике четыре минуты с YouTube, демонстрирует мастера и объясняет четко и просто Экспорт данных в Excel — [с помощью мастера экспорта для экспорта в Excel и импорта SQL Server](https://go.microsoft.com/fwlink/?linkid=829049).

-   **Дополнительные сведения о работе мастера.**

    -   **Дополнительные сведения о мастере.** Обзор мастера см. в статье [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **Сведения о подключении к источникам данных и назначения.** Если вы ищете сведения о подключении к данным, выберите нужную страницу из списка- [подключение к источникам данных с помощью мастера экспорта и импорта SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Нет отдельной странице документации для каждой из нескольких источников часто используемых данных. 

-   **Запустите мастер.** Если вы готовы запустить мастер и хотите знать, как это сделать, см. раздел [Запуск мастера экспорта и импорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

-     **Запустите мастер.** Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).




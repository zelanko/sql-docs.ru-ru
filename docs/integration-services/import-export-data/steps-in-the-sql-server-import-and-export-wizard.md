---
description: Шаги в мастере импорта и экспорта SQL Server
title: Шаги в мастере импорта и экспорта SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 06/29/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 816fb1bd-7bb9-450d-ad65-e4c2d02eaff8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69e968fbeb5f02b98393a466eadb96922b581916
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195875"
---
# <a name="steps-in-the-sql-server-import-and-export-wizard"></a>Шаги в мастере импорта и экспорта SQL Server

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


В этом разделе описывается последовательность шагов для импорта и экспорта данных с помощью мастера импорта и экспорта SQL Server. Также здесь представлены ссылки на отдельные страницы документации, содержащие описание всех страниц диалогового окна, которые отображаются в мастере.

В этом разделе описываются только **шаги** мастера. Если вам нужны другие сведения, см. раздел [Связанные задачи и содержимое](#related).

## <a name="steps-for-importing-and-exporting-data"></a>Шаги импорта и экспорта данных  
 В следующей таблице перечислены действия по импорту и экспорта данных и приведены соответствующие страницы мастера. Отображаемые страницы зависят от параметров, выбираемых в мастере.  

Чтобы кратко ознакомиться с некоторыми экранами, которые отображаются в ходе обычного сеанса мастера, просмотрите простой полный пример в разделе [Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

|Шаг|Страницы мастера|  
|----------|------------------|  
|**Добро пожаловать**<br />На этой странице никакие действия не требуются.|[Мастер импорта и экспорта SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)|  
|**Выберите источник** данных.|[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)|  
|**Выберите назначение** для данных.|[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)|  
|**Настройка назначения**. (необязательные шаги)<br /><br /> Создание целевой базы данных.<br />Если вы копируете данные в текстовый файл, настройте дополнительные параметры.|[Create Database](../../integration-services/import-export-data/create-database-sql-server-import-and-export-wizard.md)<br /><br />[Настройка назначения "Неструктурированный файл"](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)|  
|**Укажите, что требуется скопировать.**|[Выбор копирования таблицы или запроса](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)<br /><br />[Выбор исходных таблиц и представлений](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)<br /><br />[Определение исходного запроса](../../integration-services/import-export-data/provide-a-source-query-sql-server-import-and-export-wizard.md)|  
|**Настройка операции копирования**. (необязательные шаги)<br /><br /> Создание целевой таблицы.<br />— Определение действий на случай, если в мастере отсутствуют сведения о сопоставлениях типов данных между выбранными источником и назначением.<br />Проверка сопоставлений столбцов между источником и назначением.<br />Решение проблем с преобразованием типов данных между источником и назначением.<br />Просмотр данных для копирования.|[Инструкция SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md)<br /><br />[Преобразование типов без проверки](../../integration-services/import-export-data/convert-types-without-conversion-checking-sql-server-import-and-export-wizard.md)<br /><br />[Сопоставления столбцов](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)<br /><br />[Просмотр сопоставления типов данных](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)<br /><br />[Диалоговое окно "Сведения о преобразовании столбца"](../../integration-services/import-export-data/column-conversion-details-dialog-box-sql-server-import-and-export-wizard.md)<br /><br />[Диалоговое окно "Просмотр данных"](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)|  
|**Скопируйте данные.**<br /><br /> При необходимости сохраните их в виде пакета SQL Server Integration Services (SSIS).|[Сохранение и выполнение пакета](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)<br /><br />[Сохранить пакет служб SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)<br /><br />[Завершение работы мастера](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)<br /><br />[Выполнение операции](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md)|  

> [!TIP]
> Нажмите клавишу F1 при просмотре любой страницы или диалогового окна, чтобы открыть документацию по текущей странице мастера.

## <a name="related-tasks-and-content"></a><a name="related"></a> Связанные задачи и содержимое  
Ниже приведены некоторые основные задачи.
-   **См. краткий пример работы мастера.**

    -   **Ознакомьтесь со снимками экрана.** Просмотрите простой полный пример в разделе [Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Посмотрите видео.** В этом четырехминутном видео на YouTube демонстрируется работа мастера и объясняется, как с его помощью экспортировать данные в Excel: [Использование мастера импорта и экспорта SQL Server для экспорта в Excel](https://go.microsoft.com/fwlink/?linkid=829049).

-   **Дополнительные сведения о работе мастера.**

    -   **Дополнительные сведения о мастере.** Обзор мастера см. в статье [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **Сведения о подключении к источникам данных и назначениям.** Сведения о подключении к данным см. на соответствующей странице, выбрав ее в списке в разделе [Подключение к источникам данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Для каждого распространенного источника данных имеется отдельная страница документации. 

-   **Запуск мастера.** Если вы готовы запустить мастер и хотите знать, как это сделать, см. раздел [Запуск мастера экспорта и импорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

-   **Запустите мастер.** Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md).
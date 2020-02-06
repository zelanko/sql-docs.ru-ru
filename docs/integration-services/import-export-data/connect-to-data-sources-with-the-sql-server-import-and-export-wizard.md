---
title: Подключение к источникам данных с помощью мастера импорта и экспорта SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 02/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: fd726506-54b7-433b-bf70-3642235b7b31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd76d5aa66567dde3c5dc7b5ce4c2c6d787d2136
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296323"
---
# <a name="connect-to-data-sources-with-the-sql-server-import-and-export-wizard"></a>Подключение к источникам данных с помощью мастера импорта и экспорта SQL Server

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


В подразделах этого раздела показано, как подключиться к нескольким наиболее распространенным источникам данных с помощью мастера экспорта и импорта SQL Server. Вы должны предоставить сведения о подключении для источников данных на страницах **Выбор источника данных** и **Выбор назначения** мастера.

Эти подразделы описывают только **подключение к источникам данных** со страниц **Выбор источника данных** и **Выбор назначения мастера**. Если вам нужны другие сведения, см. раздел [Связанные задачи и содержимое](#related).

## <a name="connect-to-a-commonly-used-data-source"></a>Подключение к часто используемому источнику данных
Щелкните ссылку для получения дополнительных сведений о подключении к одному из следующих часто используемых источников данных.
-   [SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Неструктурированные (текстовые) файлы](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Доступ](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Хранилище BLOB-объектов Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

## <a name="connect-to-other-data-providers"></a>Подключение к другим поставщикам данных
Сведения о подключении к источникам данных, не представленным в этом списке, см. в [справочнике по строкам подключения](https://www.connectionstrings.com/). На этом стороннем сайте представлены примеры строк подключения и дополнительные сведения о поставщиках данных и используемых ими данных подключений.

## <a name="related"></a> Связанные задачи и содержимое  
Ниже приведены некоторые основные задачи.
-   **См. краткий пример работы мастера.**

    -   **Ознакомьтесь со снимками экрана.** Просмотрите простой полный пример в разделе [Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Посмотрите видео.** В этом четырехминутном видео на YouTube демонстрируется работа мастера и объясняется, как с его помощью экспортировать данные в Excel: [Использование мастера импорта и экспорта SQL Server для экспорта в Excel](https://go.microsoft.com/fwlink/?linkid=829049).

-   **Дополнительные сведения о работе мастера.**

    -   **Дополнительные сведения о мастере.** Обзор мастера см. в статье [Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **Дополнительные сведения о шагах в мастере.** Если вам нужны сведения о шагах, выполняемых в мастере, см. в разделе [Шаги в мастере импорта и экспорта SQL Server](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Каждой странице мастера соответствует отдельная страница документации.

-   **Запуск мастера.** Если вы готовы запустить мастер и хотите знать, как это сделать, см. раздел [Запуск мастера экспорта и импорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

-   **Запустите мастер.** Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="see-also"></a>См. также раздел
[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)



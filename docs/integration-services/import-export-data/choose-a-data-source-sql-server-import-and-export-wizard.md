---
title: Выбор источника данных (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b707b2b31c15c565353f0ff581ca1f4d7308a25b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71951942"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>Выбор источника данных (мастер импорта и экспорта SQL Server)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  После страницы приветствия в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется страница **Выбор источника данных**. На этой странице введите сведения об источнике данных и о том, как к нему подключиться.
  
Сведения об источниках данных, которые можно использовать, см. в разделе [Какие источники данных и назначения можно использовать](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources).

> [!NOTE]
> Мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует SQL Server Integration Services (SSIS). Таким образом, те же ограничения, которые применяются к SSIS, также применяются к мастеру.  Например, столбцы ErrorCode и ErrorColumn, которые добавляются по умолчанию, как описано в статье [Обработка ошибок в данных](../../integration-services/data-flow/error-handling-in-data.md).

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>Снимок экрана: страница "Выбор источника данных" 
На следующем рисунке показана первая часть страницы **Выбор источника данных** мастера. Число параметров в остальной части страницы зависит от выбранного источника данных.

![Выбор источника](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>Выбор источника данных
 **Источник данных**  
Укажите источник данных, выбрав поставщик данных, который может подключиться к источнику.

-   **Нужный вам поставщик данных часто можно легко распознать по имени**, так как оно обычно содержит имя источника данных, например, источник *неструктурированных файлов*, Microsoft *Excel*, Microsoft *Access*, поставщик данных .NET Framework для *SqlServer*, поставщик данных .NET Framework для *Oracle*.

-   **Если у вас есть драйвер ODBC для источника данных**, выберите поставщик данных .NET Framework для ODBC. Введите информацию о драйвере. Драйверы ODBC не приводятся в раскрывающемся списке источников данных. Поставщик данных .Net Framework для ODBC служит оболочкой для драйвера ODBC. Дополнительные сведения см. в разделе [Подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Для источника данных может существовать несколько поставщиков.** Как правило, можно выбрать любой поставщик, работающий с нужным источником данных. Например, для подключения к Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать поставщик данных .NET Framework для SQL Server или драйвер ODBC для SQL Server. (Другие поставщики по-прежнему присутствуют в списке, но уже не поддерживаются.) 

## <a name="my-data-source-isnt-in-the-list"></a>Мой источник данных отсутствует в списке
-   **Поставщик может потребоваться скачать** с веб-сайта корпорации Майкрософт или другого разработчика. Список **Источник данных** содержит только поставщики данных, которые установлены на вашем компьютере. Сведения об источниках данных, которые можно использовать, см. в разделе [Какие источники данных и назначения можно использовать](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources).

-   **У вас есть драйвер ODBC для своего источника данных?** Драйверы ODBC не приводятся в раскрывающемся списке источников данных. Если у вас есть драйвер ODBC для источника данных, выберите поставщик данных .NET Framework для ODBC. Введите информацию о драйвере. Поставщик данных .Net Framework для ODBC служит оболочкой для драйвера ODBC. Дополнительные сведения см. в разделе [Подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **64-разрядные и 32-разрядные поставщики.** Если вы используете 64-разрядный мастер, то не увидите источники данных, для которых установлен только 32-разрядный поставщик, и наоборот.

> [!NOTE]
> Чтобы использовать 64-разрядную версию мастера экспорта и импорта SQL Server, нужно установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS) являются 32-разрядными приложениями и устанавливают только 32-разрядные файлы, включая 32-разрядную версию мастера.

## <a name="after-you-choose-a-data-source"></a>После выбора источника данных
После того как вы выберете источник данных, в остальной части страницы **Выбор источника данных** отобразится определенный набор параметров, который зависит от выбранного поставщика данных.

Сведения о подключении к распространенным источникам данных см. на приведенных ниже страницах.
-   [Диалоговое окно "Подключение к SQL Server"](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Соединение с Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к неструктурированным (текстовым) файлам](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к хранилищу BLOB-объектов Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Подключение к PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Сведения о подключении к источникам данных, не представленным в этом списке, см. в [справочнике по строкам подключения](https://www.connectionstrings.com/). На этом стороннем сайте представлены примеры строк подключения и дополнительные сведения о поставщиках данных и используемых ими данных подключений.

## <a name="whats-next"></a>Дальнейшие действия
 После того как вы укажете сведения об источнике данных и о том, как к нему подключиться, откроется страница **Выбор назначения**. На этой странице введите сведения о месте назначения для данных и о том, как к нему подключиться. Дополнительные сведения см. в разделе [Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).

## <a name="see-also"></a>См. также раздел
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)

[!INCLUDE[get-help-options](../../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../../includes/paragraph-content/contribute-to-content.md)]

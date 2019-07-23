---
title: Выбор назначения (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 68f3d3c7d49d5951296e3c3cee42a7cb3299b4e2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912532"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Выбор назначения (мастер импорта и экспорта SQL Server)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


 После того как вы укажете сведения об источнике данных и о том, как к нему подключиться, в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется страница **Выбор назначения**. На этой странице введите сведения о месте назначения для данных и о том, как к нему подключиться.
  
Сведения о назначениях данных, которые можно использовать, см. в разделе [Какие источники данных и назначения можно использовать](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources). 

## <a name="screen-shot-of-the-destination-page"></a>Снимок экрана: страница "Назначение"
На следующем снимке экрана показана первая часть страницы **Выбор назначения** мастера. Число параметров в остальной части страницы зависит от выбранного здесь назначения.

![Выбор назначения](../../integration-services/import-export-data/media/choose-destination.png)

## <a name="choose-a-destination"></a>Выбор назначения
 **Назначение**  
 Укажите назначение, выбрав поставщик данных, который может импортировать данные в назначение.
 
-   **Нужный вам поставщик данных часто можно легко распознать по имени**, так как оно обычно содержит имя назначения, например назначение *неструктурированных файлов*, Microsoft *Excel*, Microsoft *Access*, поставщик данных .NET Framework для *SqlServer*, поставщик данных .NET Framework для *Oracle*.

-   **Если у вас есть драйвер ODBC для назначения**, выберите поставщик данных .NET Framework для ODBC. Введите информацию о драйвере. Драйверы ODBC не приводятся в раскрывающемся списке назначений. Поставщик данных .Net Framework для ODBC служит оболочкой для драйвера ODBC. Дополнительные сведения см. в разделе [Подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Для назначения может существовать несколько поставщиков.** Как правило, можно выбрать любой поставщик, работающий с нужным назначением. Например, для подключения к Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать поставщик данных .NET Framework для SQL Server или драйвер ODBC для SQL Server. (Другие поставщики по-прежнему присутствуют в списке, но уже не поддерживаются.) 

## <a name="my-destination-isnt-in-the-list"></a>Мое назначение отсутствует в списке
-   **Поставщик может потребоваться скачать** с веб-сайта корпорации Майкрософт или другого разработчика. Список **Назначение** содержит только поставщики данных, которые установлены на вашем компьютере. Сведения о назначениях, которые можно использовать, см. в разделе [Какие источники данных и назначения можно использовать](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources).

-   **У вас есть драйвер ODBC для своего назначения?** Драйверы ODBC не приводятся в раскрывающемся списке назначений. Если у вас есть драйвер ODBC для назначения, выберите поставщик данных .NET Framework для ODBC. Введите информацию о драйвере. Поставщик данных .Net Framework для ODBC служит оболочкой для драйвера ODBC. Дополнительные сведения см. в разделе [Подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **64-разрядные и 32-разрядные поставщики.** Если вы используете 64-разрядный мастер, то не увидите назначения, для которых установлен только 32-разрядный поставщик, и наоборот.

> [!NOTE]
> Чтобы использовать 64-разрядную версию мастера экспорта и импорта SQL Server, нужно установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS) являются 32-разрядными приложениями и устанавливают только 32-разрядные файлы, включая 32-разрядную версию мастера.

## <a name="after-you-choose-a-destination"></a>После выбора назначения
После того как вы выберете назначение, в остальной части страницы **Выбор назначения** отобразится определенный набор параметров, который зависит от выбранного поставщика данных.

Сведения о подключении к распространенным назначениям см. на приведенных ниже страницах.
-   [Диалоговое окно "Подключение к SQL Server"](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Соединение с Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к неструктурированным (текстовым) файлам](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к хранилищу BLOB-объектов Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Подключение к PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Сведения о подключении к назначениям, не представленным в этом списке, см. в [справочнике по строкам подключения](https://www.connectionstrings.com/). На этом стороннем сайте представлены примеры строк подключения и дополнительные сведения о поставщиках данных и используемых ими данных подключений.

## <a name="whats-next"></a>Дальнейшие действия  
 После того как вы укажете сведения о назначении и о том, как к нему подключиться, откроется страница **Выбор копирования таблицы или запроса**. На этой странице укажите, следует ли копировать всю таблицу или только определенные строки. Дополнительные сведения см. в разделе [Выбор копирования таблицы или запроса](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>См. также раздел
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



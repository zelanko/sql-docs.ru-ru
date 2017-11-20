---
title: "Выбор назначения (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 104
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 4ff3c7c8413bd6b535e1c5f95e2a7b06b397c053
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Выбор назначения (мастер импорта и экспорта SQL Server)
 После того как вы укажете сведения об источнике данных и о том, как к нему подключиться, в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется страница **Выбор назначения**. На этой странице введите сведения о месте назначения для данных и о том, как к нему подключиться.
  
Сведения о назначениях данных, которые можно использовать, см. в разделе [Какие источники данных и назначения можно использовать](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources). 

## <a name="screen-shot-of-the-destination-page"></a>Снимок экрана: страница "Назначение"
На следующем снимке экрана показана первая часть страницы **Выбор назначения** мастера. Остальная часть страницы имеет переменное число параметров, зависящее от назначения параметра.

![Выбор назначения](../../integration-services/import-export-data/media/choose-destination.png)

## <a name="choose-a-destination"></a>Выбор назначения
 **Назначение**  
 Укажите назначение, выбрав поставщик данных, который может импортировать данные в назначение.
 
-   **Обычно очевидны из его имени поставщика данных, который требуется**, так как имя поставщика обычно содержит имя назначение — например, *неструктурированного файла* назначения, корпорация Майкрософт *Excel*, Microsoft *доступа*, .net Framework поставщик данных для *SqlServer*, .net Framework поставщик данных для *Oracle*.

-   **При наличии драйвера ODBC для конечную папку**, установите .net Framework поставщика данных для ODBC. Введите информацию драйвера. В раскрывающемся списке мест назначения, отсутствуют в списке драйверов ODBC. .Net Framework поставщика данных для ODBC служит оболочкой вокруг драйвера ODBC. Дополнительные сведения см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Для назначения может существовать несколько поставщиков.** Как правило, можно выбрать любой поставщик, работающий с нужным назначением. Например, для подключения к Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно использовать поставщик данных .NET Framework для SQL Server или драйвер ODBC для SQL Server. (Другие поставщики по-прежнему находятся в списке, но больше не поддерживаются.) 

## <a name="my-destination-isnt-in-the-list"></a>Мои назначения отсутствует в списке
-   **Может потребоваться загрузить поставщик данных** от корпорации Майкрософт или у сторонних разработчиков. Список поставщиков данных, доступных в **назначения** список включает только поставщиков, установленных на компьютере. Сведения о назначениях, которые можно использовать в разделе [какие источники данных и назначения можно использовать?](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **Имеется драйвер ODBC для конечную папку?** В раскрывающемся списке мест назначения, отсутствуют в списке драйверов ODBC. При наличии драйвера ODBC для пункта назначения, установите .net Framework поставщика данных для ODBC. Введите информацию драйвера. .Net Framework поставщика данных для ODBC служит оболочкой вокруг драйвера ODBC. Дополнительные сведения см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **64-разрядных и 32-разрядные поставщики.** Если вы используете 64-разрядный мастер, вы не увидите назначения для установки 32-разрядного поставщика и наоборот.

> [!NOTE]
> Чтобы использовать 64-разрядной версии мастера экспорта и импорта SQL Server, необходимо установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS), 32-разрядных приложений и установить только 32-разрядных файлов, включая 32-разрядную версию мастера.

## <a name="after-you-choose-a-destination"></a>После выбора назначения
После выбора назначения, а остальная часть **Выбор назначения** страница имеет переменное число параметров, которые зависят от выбранного поставщика данных.

Чтобы подключиться к часто используемые назначения, см. следующие страницы.
-   [Подключение к SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к базе данных Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Подключиться к неструктурированным файлам (текстовые файлы)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Подключиться к Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Подключения ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к службе хранилища BLOB-объектов Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Подключиться к PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Сведения о подключении в место назначения, не указанного в этом разделе [Reference строки соединения](https://www.connectionstrings.com/). Этот сайт стороннего содержит примеры строк подключения и Дополнительные сведения о поставщиках данных и сведений о соединении, которые необходимы.

## <a name="whats-next"></a>Дальнейшие действия  
 После того как вы укажете сведения о назначении и о том, как к нему подключиться, откроется страница **Выбор копирования таблицы или запроса**. На этой странице укажите, следует ли копировать всю таблицу или только определенные строки. Дополнительные сведения см. в разделе [Выбор копирования таблицы или запроса](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>См. также:
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)




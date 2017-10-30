---
title: "Выбор источника данных (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 124
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 80d35cb294fd900611c73ca37bba2a66baef0767
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>Выбор источника данных (мастер импорта и экспорта SQL Server)
  После страницы приветствия в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется страница **Выбор источника данных**. На этой странице введите сведения об источнике данных и о том, как к нему подключиться.
  
Сведения об источниках данных, которые можно использовать, см. в разделе [Какие источники данных и назначения можно использовать](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources).

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>Снимок экрана: страница "Выбор источника данных" 
На следующем снимке экрана показана первая часть страницы **Выбор источника данных** мастера. Остальная часть страницы имеет переменное число параметров, зависящее от источника данных, нажмите кнопку ниже.

![Выбор источника](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>Выбор источника данных
 **Источник данных**  
Укажите источник данных, выбрав поставщик данных, который может подключиться к источнику.

-   **Обычно очевидны из его имени поставщика данных, который требуется**, так как имя поставщика обычно содержит имя источника данных — например, *неструктурированного файла* источника, корпорация Майкрософт *Excel*, Microsoft *доступа*, .net Framework поставщик данных для *SqlServer*, .net Framework поставщик данных для *Oracle*.

-   **Если имеется драйвер ODBC для источника данных**, установите .net Framework поставщика данных для ODBC. Введите информацию драйвера. Драйверы ODBC не перечислены в раскрывающемся списке источников данных. .Net Framework поставщика данных для ODBC служит оболочкой вокруг драйвера ODBC. Дополнительные сведения см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Для источника данных может существовать несколько поставщиков.** Как правило, можно выбрать любой поставщик, работающий с нужным источником данных. Например, для подключения к Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно использовать поставщик данных .NET Framework для SQL Server или драйвер ODBC для SQL Server. (Другие поставщики по-прежнему находятся в списке, но больше не поддерживаются.) 

## <a name="my-data-source-isnt-in-the-list"></a>Источник данных отсутствует в списке
-   **Может потребоваться загрузить поставщик данных** от корпорации Майкрософт или у сторонних разработчиков. Список поставщиков данных, доступных в **источника данных** список включает только поставщиков, установленных на компьютере. Сведения об источниках данных, которые можно использовать, см. в разделе [Какие источники данных и назначения можно использовать](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources).

-   **Имеется драйвер ODBC для источника данных?** Драйверы ODBC не перечислены в раскрывающемся списке источников данных. Если драйвер ODBC для источника данных, установите .net Framework поставщика данных для ODBC. Введите информацию драйвера. .Net Framework поставщика данных для ODBC служит оболочкой вокруг драйвера ODBC. Дополнительные сведения см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **64-разрядных и 32-разрядные поставщики.** Если вы используете 64-разрядный мастер, вы не увидите источников данных для установки 32-разрядного поставщика и наоборот.

> [!NOTE]
> Чтобы использовать 64-разрядной версии мастера экспорта и импорта SQL Server, необходимо установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS), 32-разрядных приложений и установить только 32-разрядных файлов, включая 32-разрядную версию мастера.

## <a name="after-you-choose-a-data-source"></a>После выбора источника данных
После выбора источника данных, остальная часть **выберите источник данных** страница имеет переменное число параметров, которые зависят от выбранного поставщика данных.

Для подключения к источнику данных часто используемые см. в одном из следующих страниц.
-   [Подключение к SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к базе данных Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Подключиться к неструктурированным файлам (текстовые файлы)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Подключиться к Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Подключения ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к службе хранилища BLOB-объектов Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Подключиться к PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Сведения о подключении к источнику данных, не указанного в этом разделе [Reference строки соединения](https://www.connectionstrings.com/). Этот сайт стороннего содержит примеры строк подключения и Дополнительные сведения о поставщиках данных и сведений о соединении, которые необходимы.

## <a name="whats-next"></a>Дальнейшие действия  
 После того как вы укажете сведения об источнике данных и о том, как к нему подключиться, откроется страница **Выбор назначения**. На этой странице введите сведения о месте назначения для данных и о том, как к нему подключиться. Дополнительные сведения см. в разделе [Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).
 
## <a name="see-also"></a>См. также:
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)




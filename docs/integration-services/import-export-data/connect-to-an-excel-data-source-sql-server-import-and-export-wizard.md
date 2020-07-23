---
title: Подключение к источнику данных Excel (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 04/02/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3a017d8de23da9297062e1d232ea86ad2aabb25a
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920000"
---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Подключение к источнику данных Excel (мастер импорта и экспорта SQL Server)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


В этой статье показано, как подключаться к источникам данных **Microsoft Excel** со страницы **Выбор источника данных** или **Выбор назначения** в мастере импорта и экспорта SQL Server.

На следующем снимке экрана показан пример подключения к книге Microsoft Excel.

![Подключение через Excel](../../integration-services/import-export-data/media/excel-connection.png) 

Для подключения к файлам Excel может потребоваться скачать и установить дополнительные файлы. Дополнительные сведения см. в разделе [Получение файлов, необходимых для подключения к Excel](../load-data-to-from-excel-with-ssis.md#files-you-need).

> [!IMPORTANT]
> Дополнительные сведения о подключении к файлам Excel, а также об ограничениях и известных проблемах, связанных с загрузкой данных в файлы этого приложения и из них, см. в разделе [Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).

## <a name="options-to-specify"></a>Указываемые параметры

> [!NOTE]
> Параметры подключения для этого поставщика данных одинаковы независимо от того, является ли Excel источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

**Путь к файлу Excel**  
 Укажите полный путь и имя для файла Excel. Пример:
-   Для файла на локальном компьютере **C:\\MyData.xlsx**.
-   Для файла в общей сетевой папке **\\\\Sales\\Database\\Northwind.xlsx**.

или нажмите **Обзор**.  
  
 **Обзор**  
 Выберите электронную таблицу с помощью диалогового окна **Открыть**.  

> [!NOTE]
> Мастер не может открыть защищенный паролем файл Excel.

 **Версия Excel**  
Выберите версию Excel для исходной или целевой рабочей книги.

**Первая строка содержит имена столбцов**  
Укажите, содержит ли первая строка данных имена столбцов.
-   Если данные содержат имена столбцов, но этот параметр включен, мастер рассматривает первую строку исходных данных как имена столбцов.
-   Если данные содержат имена столбцов, но этот параметр отключен, мастер рассматривает строку имен столбцов как первую строку данных.

Если указать, что в данных отсутствуют имена столбцов, мастер внутренним образом использует F1, F2 и т. д. в качестве таких заголовков.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel не отображается в списке источников данных
Если вы не видите Excel в списке источников данных, определите, не используете ли вы 64-разрядный мастер? Поставщики для Excel и Access обычно 32-разрядные и поэтому не отображаются в 64-разрядном мастере. Запустите 32-разрядный мастер.

> [!NOTE]
> Чтобы использовать 64-разрядную версию мастера экспорта и импорта SQL Server, нужно установить SQL Server. SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS) являются 32-разрядными приложениями и устанавливают только 32-разрядные файлы, включая 32-разрядную версию мастера.

## <a name="see-also"></a>См. также раздел
[Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


---
title: "Импорт и экспорт данных с помощью мастера экспорта и импорта SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 160
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 6cd388215de02072522011b149a9cecc3239b64c
ms.contentlocale: ru-ru
ms.lasthandoff: 10/18/2017

---
# <a name="import-and-export-data-with-the-sql-server-import-and-export-wizard"></a>Импорт и экспорт данных с помощью мастера импорта и экспорта SQL Server

 > Содержимое, связанное с предыдущих версий SQL Server, в разделе [запустить мастер экспорта и импорта SQL Server](https://msdn.microsoft.com/en-US/library/ms140052(SQL.120).aspx).

 Мастер импорта и экспорта[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет простой способ копирования данных из источника в целевой объект. В этом обзоре описываются источники данных, которые мастер можно использовать в качестве источников и назначений, а также разрешения, необходимые для запуска мастера.

## <a name="get-the-wizard"></a>Получить мастера
Если вы хотите запустить мастер, но на вашем компьютере не установлен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно установить с помощью SQL Server Data Tools (SSDT). Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="what-happens-when-i-run-the-wizard"></a>Что происходит при запуске мастера?
-    **См. список шагов.** Описание действия в мастере см. в разделе [шаги в мастере экспорта и импорта SQL Server](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Имеется также отдельной странице документации для каждой страницы мастера.  
    \- или \-
-   **Пример см.** Для быстрого просмотра на нескольких экранах, см в сеансе типичные, взгляните на этот простой пример на одной странице - [Приступая к работе с простой пример мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).  

##  <a name="wizardSources"></a>Какие источники и назначения можно использовать?  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Мастера импорта и экспорта можно копировать данные из источников данных, перечислены в следующей таблице. Чтобы подключиться к некоторым из этих источников данных, может потребоваться загрузка и установка дополнительных файлов.
 
| Источник данных | Нужно ли скачивать дополнительные файлы? |
|-------------|-----------------------------------------|
|**Базы данных корпоративного класса**<br/>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle, DB2 и другие.|SQL Server или SQL Server Data Tools (SSDT) устанавливает файлы, необходимые для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако SSDT не устанавливает файлы, необходимые для подключения к другим базам данных предприятия, например Oracle или IBM DB2.<br/><br/>Чтобы подключиться к корпоративной базе данных, обычно нужно иметь две вещи:<br/><br/>1. **Клиентское программное обеспечение**. Если для корпоративной системы баз данных уже установлено клиентское программное обеспечение, то, как правило, у вас есть все необходимое для установки соединения. Если клиентское программное обеспечение не установлено, обратитесь к администратору базы данных по поводу установки лицензионной копии.<br/><br/>2. **Драйверы и поставщики**. Microsoft устанавливает драйверы и поставщики для подключения к базе данных Oracle. Для подключения IBM DB2, получить поставщик Microsoft® OLEDB для DB2 v5.0 для Microsoft SQL Server из [пакет дополнительных компонентов Microsoft SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=52676).<br/><br/>Дополнительные сведения см. в разделе [подключение к источнику данных SQL Server](connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md) или [подключение к источнику данных Oracle](connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md).|
|**Текстовые файлы** (неструктурированных файлов)|Никакие дополнительные файлы не требуются.<br/><br/>Дополнительные сведения см. в разделе [соединение с источником данных неструктурированного файла](connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md).|
|**Файлы Microsoft Excel и Microsoft Access**|Microsoft Office не устанавливает все файлы, необходимые для подключения к файлам Excel и Access в качестве источников данных. Скачайте следующие - [доступа к базе данных ядро 2016 распространяемый компонент Microsoft](https://www.microsoft.com/download/details.aspx?id=54920).<br/><br/>Дополнительные сведения см. в разделе [соединение с источником данных Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md) или [подключение к источнику данных Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md).|
|**Источники данных Azure**<br/>В настоящее время доступно только хранилище BLOB-объектов Azure.|SQL Server Data Tools не устанавливать файлы, необходимые для подключения к хранилищу больших двоичных объектов Azure в качестве источника данных. Скачайте [пакет дополнительных компонентов служб SQL Server Integration Services 2016 для Azure](https://www.microsoft.com/download/details.aspx?id=49492).<br/><br/>Дополнительные сведения см. в разделе [подключение к хранилищу Azure блог](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md).|
|**Базы данных с открытым исходным кодом**<br/>PostgreSQL, MySql и др.|Для подключения к источникам данных, вам придется загружать дополнительные файлы.<br/><br/>— Для **PostgreSQL**, в разделе [соединение с источником данных PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md).<br/>— Для **MySql**, в разделе [соединение с источником данных MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md).|
|**Любой другой источник данных, для которой имеется драйвер или поставщик**|Обычно для подключения к указанным ниже источникам данных требуется скачать дополнительные файлы.<br/><br/>Любой источник, для которого доступен **драйвер ODBC** . Дополнительные сведения см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).<br/>Любой источник, для которого доступен **поставщик данных .NET Framework** .<br/>Любой источник, для которого доступен **поставщик OLE DB** .<br/><br/>Сторонние компоненты, которые обеспечивают возможности источника и назначения для других источников данных иногда продаваемые продуктов через дополнительные компоненты для SQL Server Integration Services (SSIS).|

## <a name="how-do-i-connect-to-my-data"></a>Как подключаться Мои данные?
Сведения о подключении к источнику данных часто используемые см. в одном из следующих страниц:
-   [Диалоговое окно "Подключение к SQL Server"](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Соединение с Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Подключиться к неструктурированным файлам (текстовые файлы)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Подключиться к Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к службе хранилища BLOB-объектов Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Подключения ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Подключиться к PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Подключение к MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)


Сведения о подключении к источнику данных, не указанного в этом разделе [Reference строки соединения](https://www.connectionstrings.com/). Этот сайт стороннего содержит примеры строк подключения и Дополнительные сведения о поставщиках данных и сведений о соединении, которые необходимы.

## <a name="what-permissions-do-i-need"></a>Какие разрешения следует предпринять?  
 Чтобы успешно запустить мастер импорта и экспорта служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , нужно иметь по крайней мере одно из указанных ниже разрешений. Если вы уже работаете с источником данных и назначением, вероятно, у вас уже есть нужные разрешения.
  
|Задачи, для выполнения которых требуются разрешения|При подключении к SQL Server, необходимо, чтобы эти разрешения |  
|-------------------------|----------------------------------------------------|  
|Подключение к исходным и целевым базам данных, а также к общим папкам.|Права на вход в систему сервера и базы данных.|  
|Экспорт или считывание данных из исходной базы данных или файла.|Разрешения SELECT на исходные таблицы и представления.|  
|Импорт или запись данных в целевую базу данных или файл.|Разрешения INSERT для целевых таблиц.|  
|Создание целевой базы данных или файла, если это применимо.|Разрешения CREATE DATABASE или CREATE TABLE.|  
|Сохранение пакета служб SSIS, созданного с помощью мастера, если применимо.|Если вы хотите сохранить пакет в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], достаточно разрешений для сохранения пакета в базу данных **msdb** .|  
  
## <a name="get-help-while-the-wizard-is-running"></a>Получение справки во время работы мастера
> [!TIP]
> Нажмите клавишу F1 при просмотре любой страницы или диалогового окна, чтобы открыть документацию по текущей странице мастера.   
  
##  <a name="wizardSSIS"></a> Мастер использует службы SQL Server Integration Services  
 Мастер использует службы SQL Server Integration Services (SSIS) для копирования данных. Службы SSIS — это средство для извлечения, преобразования и загрузки данных (ETL). Страницы мастера используют некоторые фрагменты языка служб SSIS.
  
 В службах SSIS основной единицей является **пакет**. По мере перемещения по страницам и указания параметров мастер создает пакет служб SSIS в памяти.    
  
Если установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition или более поздний выпуск, можно при необходимости сохранить пакет SSIS. В дальнейшем при помощи конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] можно повторно использовать пакет или расширить его, включив дополнительные задачи, преобразования и логику обработки событий. Мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является простейшим методом создания базового пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , копирующего данные из источника в назначение.

Дополнительные сведения о службах SSIS см. в разделе [Службы SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).

## <a name="whats-next"></a>Дальнейшие действия  
 Запустите мастер. Дополнительные сведения см. в разделе [Запуск мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>См. также:
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)  
[Сопоставление типов данных в мастере импорта и экспорта SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)




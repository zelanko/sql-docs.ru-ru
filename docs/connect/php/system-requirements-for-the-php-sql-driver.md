---
title: Системные требования драйверов Майкрософт для PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b601d4fbb02b489aca228acb719cfe8bad834dc0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992567"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Системные требования драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этом документе перечислены компоненты, которые должны быть установлены в системе для доступа к данным в SQL Server или базе данных SQL Azure с [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]помощью.

Официально поддерживаются версии 3,1 и более поздних версий драйверов Microsoft PHP для SQL Server. Полные сведения о жизненных циклах поддержки и требованиях, включая более ранние версии драйверов PHP, см. в таблице [поддержки](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Сведения о том, как скачать и установить актуальные и стабильные двоичные файлы, см. на [веб-сайте PHP](https://php.net).  Для использования драйверов Microsoft PHP для SQL Server требуются следующие версии PHP:

|Версия драйвера PHP для SQL Server&#8594;<br />&#8595; версия PHP|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|:---:|---|---|---|---|---|---|---|
|7.3|7.3.0+ | | | | | | |
|7.2|7.2+<sup>1</sup>|7.2+<sup>1</sup>|7.2+<sup>1</sup>| | | | |
|7.1|7.1.0+ |7.1.0+ |7.1.0+ |7.1.0+ |       |        |        |
|7.0|       |7.0.0+ |7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |       |       |5.6.4+  |        |
|5.5|       |       |       |       |       |5.5.16+ |5.5.16+ |
|5.4|       |       |       |       |       |5.4.32  |5.4.32  |

1. Версии 7.2.1 и более поздних версий поддерживаются в Windows, а версии 7.2.0 и более поздних поддерживаются в Linux и macOS.

-   Версия файла драйвера должна находиться в каталоге расширения PHP. Сведения о различных файлах драйверов см. в разделе [версии драйверов](#driver-versions) .  Сведения о скачивании драйверов см. в статье [Драйверы Майкрософт для PHP для SQL Server](../../connect/php/download-drivers-php-sql-server.md). Сведения о настройке драйвера для PHP см. в статье [Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md).

-   Требуется веб-сервер. Веб-сервер должен быть настроен на выполнение PHP. Сведения о размещении приложений PHP с IIS см. в [руководстве на веб-сайте PHP](http://docs.php.net/manual/da/install.windows.iis7.php).

    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] был протестирован в службе IIS 10 с помощью FastCGI.  

    > [!NOTE]  
    > Корпорация Майкрософт обеспечивает поддержку только для служб IIS.  

## <a name="odbc-driver"></a>Драйвер ODBC

На компьютере, на котором работает PHP, требуется правильная версия Microsoft ODBC Driver for SQL Server. На [этой странице](https://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-2017)можно скачать все поддерживаемые версии драйвера для поддерживаемых платформ.

Если вы скачиваете версию драйвера для Windows в 64-разрядной версии Windows, установщик ODBC 64-bit устанавливает как 32-разрядные, так и 64-разрядные драйверы ODBC. При использовании 32-разрядной версии Windows используйте установщик ODBC x86. На платформах, отличных от Windows, доступны только 64-разрядные версии драйвера.

|Версия драйвера PHP для SQL Server&#8594;<br />&#8595; Версия драйвера ODBC|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Драйвер ODBC 17+ |Да|Да|Да| | | | |
|Драйвер ODBC 13.1|Да|Да|Да|Да|Да| | |
|Драйвер ODBC 13  | | | | |Да| | |
|Драйвер ODBC 11  |Да|Да|Да|Да|Да|Да|Да|

Если используется драйвер sqlsrv, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) возвращает сведения о версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft ODBC Driver for SQL Server, используемой. [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Если вы используете драйвер PDO_SQLSRV, можно применить [PDO::getAttribute](../../connect/php/pdo-getattribute.md) для определения версии.  

## <a name="sql-server"></a>SQL Server

Поддерживаются базы данных SQL Azure. Дополнительные сведения см. в статье [Подключение к базе данных Microsoft Azure SQL](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|Версия драйвера PHP для SQL Server&#8594;<br />&#8595; версия SQL Server|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|База данных SQL Azure        |Да|Да|Да|Да| | | |
|Управляемый экземпляр SQL Azure|Да|Да|Да|Да| | | |
|Хранилище данных SQL Azure  |Да|Да|Да|Да| | | |
|SQL Server 2017           |Да|Да|Да|Да| | | |
|SQL Server 2016           |Да|Да|Да|Да|Да| | |
|SQL Server 2014           |Да|Да|Да|Да|Да|Да|Да|
|SQL Server 2012           |Да|Да|Да|Да|Да|Да|Да|
|SQL Server 2008 R2        |Да|Да|Да|Да|Да|Да|Да|
|SQL Server 2008           | | | | |Да|Да|Да|

## <a name="operating-systems"></a>Операционные системы
Для каждой версии драйвера поддерживаются следующие операционные системы:

|Версия драйвера PHP для SQL Server&#8594;<br />&#8595; операционная система|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Windows Server 2016                 |Да  |Да  |Да  |Да  |   |   |   |
|Windows Server 2012 R2              |Да  |Да  |Да  |Да  |Да  |Да  |Да  |
|Windows Server 2012                 |Да  |Да  |Да  |Да  |Да  |Да  |Да  |
|Windows Server 2008 R2 с пакетом обновления 1 (SP1)          |   |   |   |   |Да  |Да  |Да  |
|Windows Server 2008 с пакетом обновления 2 (SP2)             |   |   |   |   |Да  |Да  |Да  |
|Windows 10                          |Да  |Да  |Да  |Да  |Да  |   |   |
|Windows 8.1                         |Да  |Да  |Да  |Да  |Да  |Да  |Да  |
|Windows 8                           |   |   |   |Да  |Да  |Да  |Да  |
|Windows 7 с пакетом обновления 1 (SP1)                       |   |   |   |   |Да  |Да  |Да  |
|Windows Vista с пакетом обновления 2 (SP2)                   |   |   |   |   |Да  |Да  |Да  |
|Ubuntu 18,10 (64-разрядная версия)               |Да  |   |   |   |   |   |   |
|Ubuntu 18,04 (64-разрядная версия)               |Да  |Да  |   |   |   |   |   |
|Ubuntu 17,10 (64-разрядная версия)               |   |Да  |Да  |   |   |   |   |
|Ubuntu 16,04 (64-разрядная версия)               |Да  |Да  |Да  |Да  |Да  |   |   |
|Ubuntu 15,10 (64-разрядная версия)               |   |   |   |Да  |   |   |   |
|Ubuntu 15,04 (64-разрядная версия)               |   |   |   |   |Да  |   |   |
|Debian 9 (64-разрядная версия)                   |Да  |Да  |Да  |   |   |   |   |
|Debian 8 (64-разрядная версия)                   |Да  |Да  |Да  |Да  |   |   |   |
|Red Hat Enterprise Linux 7 (64-разрядная версия) |Да  |Да  |Да  |Да  |Да  |   |   |
|SUSE Enterprise Linux 15 (64-разрядная версия)   |Да  |   |   |   |   |   |   |
|SUSE Enterprise Linux 12 (64-разрядная версия)   |Да  |Да  |Да  |   |   |   |   |
|macOS Можаве (64-разрядная версия)               |Да  |   |   |   |   |   |   |
|macOS High Сьерра (64-разрядный)          |Да  |Да  |   |   |   |   |   |
|macOS Sierra (64-разрядная)               |Да  |Да  |Да  |Да  |   |   |   |
|macOS El Capitan (64-разрядная версия)           |   |Да  |Да  |Да  |   |   |   |

## <a name="driver-versions"></a>Версии драйвера  
В этом разделе перечислены файлы драйверов, которые входят в состав каждой версии [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Каждый пакет установки содержит файлы драйверов SQLSRV и PDO_SQLSRV в потоковых и непотоковых вариантах. В Windows они также доступны в 32-разрядных и 64-разрядных вариантах. Чтобы настроить драйвер для использования в среде выполнения PHP, следуйте инструкциям по установке, приведенным в статье [Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md).

В поддерживаемых версиях Linux и macOS соответствующие драйверы можно установить с помощью системы пакетов PECL для PHP, следуя [инструкциям по установке Linux и macOS](../../connect/php/installation-tutorial-linux-mac.md). Кроме того, вы можете скачать предварительно созданные двоичные файлы для платформы с помощью [драйверов Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) странице проекта GitHub. в приведенных ниже таблицах перечислены файлы, найденные в предварительно созданных двоичных пакетах.

**Драйверы Майкрософт версии 5.6 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядная php7ts. dll|   
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_72_ts.dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_72_ts.dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|да|64-разрядная php7ts. dll|  
|32-bit php_sqlsrv_73_nts.dll<br />32-bit php_pdo_sqlsrv_73_nts.dll|7.3|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_73_ts.dll <br />32-bit php_pdo_sqlsrv_73_ts.dll |7.3|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_73_nts.dll<br />64-bit php_pdo_sqlsrv_73_nts.dll|7.3|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_73_ts.dll <br />64-bit php_pdo_sqlsrv_73_ts.dll |7.3|да|64-разрядная php7ts. dll|  

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|нет |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|да|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|нет |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|да|
|php_sqlsrv_73_nts.so<br />php_pdo_sqlsrv_73_nts.so|7.3|нет |
|php_sqlsrv_73_ts.so <br />php_pdo_sqlsrv_73_ts.so |7.3|да|

**Драйверы Майкрософт версии 5.3 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядная Php7. dll|
|32-bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядная php7ts. dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_7_ts.dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядная php7ts. dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядная php7ts. dll|   
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_72_ts.dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_72_ts.dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|да|64-разрядная php7ts. dll|  

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|нет |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|да|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|нет |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|да|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|нет |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|да|

**Драйверы Майкрософт версии 5.2 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядная Php7. dll|
|32-bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядная php7ts. dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_7_ts.dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядная php7ts. dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядная php7ts. dll|   
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_72_ts.dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_72_ts.dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|да|64-разрядная php7ts. dll|  

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|нет |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|да|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|нет |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|да|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|нет |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|да|

**Драйверы Майкрософт версии 4.3 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядная Php7. dll|
|32-bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядная php7ts. dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_7_ts.dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядная php7ts. dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядная Php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядная php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядная Php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядная php7ts. dll|   

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|нет |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|да|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|нет |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|да|  

**Драйверы Майкрософт версии 4.0 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|нет|32-разрядная Php7. dll|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|да|32-разрядная php7ts. dll|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|нет|64-разрядная Php7. dll|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|да|64-разрядная php7ts. dll|   

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|нет |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|да|

**Драйверы Майкрософт версии 3.2 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|нет|php5.dll|  
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|да|php5ts.dll|  

**Драйверы Майкрософт версии 3.1 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  

## <a name="see-also"></a>См. также:  
[Getting Started with the Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md) (Начало работы с драйверами Майкрософт для PHP для SQL Server)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по API драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  

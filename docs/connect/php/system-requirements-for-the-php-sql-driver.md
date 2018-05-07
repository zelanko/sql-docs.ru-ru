---
title: Требования к системе для драйвера Microsoft PHP для SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/23/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: 93
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c1eae99587a1f447b809becee9509d5a04136e3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Требования к системе для драйвера Microsoft PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этом документе перечислены компоненты, которые должны быть установлены на компьютере, чтобы получить доступ к данным в SQL Server или база данных SQL Azure с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

Официально поддерживаются версии 3.1 и более поздних версий драйверы Microsoft PHP для SQL Server. Полные сведения о жизненных циклах поддержки и требования, включая более ранние версии драйверов PHP. в разделе [Матрица поддержки](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Сведения о том, как загрузить и установить последнюю стабильные двоичные файлы PHP см. в разделе [веб-сайта PHP](http://php.net).  Драйверы Майкрософт для PHP для SQL Server требуются следующие версии PHP:

|PHP для SQL Server версии драйвера&#8594;<br />&#8595;Версия PHP|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|7.2|7.2.1+ в Windows<br/>7.2.0+ на других платформах | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |5.6.4+  |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |
|5.4|       |       |       |5.4.32  |5.4.32  |

-   Версия файла драйвера должна находиться в каталоге расширения PHP. В разделе [версии драйверов](#driver-versions) сведения о разных файлах драйвера.  Загрузить драйверы [загрузить драйверы Майкрософт для PHP для SQL Server](download-drivers-php-sql-server.md). Сведения о настройке драйвера для PHP см. в разделе [загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md).

-   Требуется веб-сервер. Веб-сервер должен быть настроен на выполнение PHP. Сведения о размещении приложений PHP в службах IIS см. в разделе [учебник на веб-сайта PHP в](http://php.net/manual/fa/install.windows.iis.php).  

    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Протестирована IIS 10 с помощью FastCGI.  

    > [!NOTE]  
    > Корпорация Майкрософт обеспечивает поддержку только для служб IIS.  

## <a name="odbc-driver"></a>Драйвер ODBC

Требуется правильная версия драйвера Microsoft ODBC для SQL Server на компьютере, на котором выполняется PHP. Загрузите по следующим ссылкам:
- [17 драйвера Microsoft ODBC для SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=56567)
- [Microsoft ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=53339)
- [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)
- [Драйвер Microsoft ODBC 11 для SQL Server](http://www.microsoft.com/download/details.aspx?id=36434)

При использовании 64-разрядной операционной системе ODBC 64-разрядный установщик устанавливает 32-разрядных и 64-разрядные драйверы ODBC. Если вы используете 32-разрядной операционной системе, используйте ODBC x86 установщика.

|PHP для SQL Server версии драйвера&#8594;<br />&#8595;Версия драйвера ODBC|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Драйвер ODBC 17  |Да| | | | |
|ODBC Driver 13.1|Да|Да|Да| | |
|ODBC Driver 13  | | |Да| | |
|ODBC Driver 11  |Да|Да|Да|Да|Да|

Если вы используете драйвер SQLSRV, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) возвращает сведения о версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] драйвер ODBC для SQL Server используется [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Если вы используете драйвер PDO_SQLSRV, можно использовать [PDO::getAttribute](../../connect/php/pdo-getattribute.md) для обнаружения версии.  

## <a name="sql-server"></a>SQL Server

Поддерживаются базы данных SQL Azure. Сведения см. в разделе [подключение к базе данных SQL Microsoft Azure](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|PHP для SQL Server версии драйвера&#8594;<br />&#8595;Версия SQL Server|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Управляемый экземпляр Azure SQL<br/> (Расширенный набор личной предварительной версии)|Да|Да| | | |
|Хранилище данных SQL Azure|Да|Да| | | |
|SQL Server 2017   |Да|Да| | | |
|SQL Server 2016   |Да|Да|Да| | |
|SQL Server 2014   |Да|Да|Да|Да|Да|
|SQL Server 2012   |Да|Да|Да|Да|Да|
|SQL Server 2008 R2|Да|Да|Да|Да|Да|
|SQL Server 2008   | | |Да|Да|Да|

## <a name="operating-systems"></a>Операционные системы
Ниже приведены поддерживаемые операционные системы для версии драйвера:

|PHP для SQL Server версии драйвера&#8594;<br />&#8595;Операционная система|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Windows Server 2016                      |Да|Да| | | |
|Windows Server 2012 R2                   |Да|Да|Да|Да|Да|
|Windows Server 2012                      |Да|Да|Да|Да|Да|
|Windows Server 2008 R2 с пакетом обновления 1 (SP1)               | | |Да|Да|Да|
|Windows Server 2008 с пакетом обновления 2 (SP2)                  | | |Да|Да|Да|
|Windows 10                               |Да|Да|Да| | |
|Windows 8.1                              |Да|Да|Да|Да|Да|
|Windows 8                                | |Да|Да|Да|Да|
|Windows 7 с пакетом обновления 1 (SP1)                            | | |Да|Да|Да|
|Windows Vista с пакетом обновления 2 (SP2)                        | | |Да|Да|Да|
|Ubuntu 17.10 (64-разрядная версия)                    |Да| | | | |
|Ubuntu 16.04 (64-разрядная версия)                    |Да|Да|Да| | |
|Ubuntu 15.10 (64-разрядная версия)                    | |Да| | | |
|Ubuntu 15.04 (64-разрядная версия)                    | | |Да| | |
|Debian 9 (64-разрядная версия)                        |Да| | | | |
|Debian 8 (64-разрядная версия)                        |Да|Да| | | |
|Red Hat Enterprise Linux 7 (64-разрядная версия)      |Да|Да|Да| | |
|Linux SuSE Enterprise 12 (64-разрядная версия)        |Да| | | | |
|macOS Сьерра (64-разрядная версия)                    |Да|Да| | | |
|macOS Capitan El (64-разрядная версия)                |Да|Да| | | |

## <a name="driver-versions"></a>Версии драйвера  
В этом разделе перечислены файлов драйверов, которые входят в состав каждой версии [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Каждый пакет установки содержит файлы драйвера SQLSRV и PDO_SQLSRV потоками и однопоточных варианты. В Windows они также доступны в виде 32-разрядных и 64-разрядных Variant. Чтобы настроить драйвер для использования в среде выполнения PHP, выполните инструкции по установке в [загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md).

В поддерживаемые версии Linux и macOS необходимые драйверы можно установить с помощью PHP нагрузка PECL пакета системы, после [Linux и macOS инструкции по установке](../../connect/php/installation-tutorial-linux-mac.md). Кроме того, можно загрузить предварительно подготовленный двоичные файлы для вашей платформы из [драйверы Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) странице Github проекта--в таблицах ниже перечислены файлы, обнаруженные в готовых двоичных пакетов.

**Драйверы Microsoft 5.2 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|32-разрядное php_sqlsrv_7_nts.dll <br />32-разрядное php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядное php7.dll|
|32-разрядное php_sqlsrv_7_ts.dll  <br />32-разрядное php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядное php7ts.dll|
|64-разрядной php_sqlsrv_7_nts.dll <br />64-разрядной php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядной php7.dll|  
|64-разрядной php_sqlsrv_7_ts.dll  <br />64-разрядной php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядной php7ts.dll|
|32-разрядное php_sqlsrv_71_nts.dll<br />32-разрядное php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядное php7.dll|  
|32-разрядное php_sqlsrv_71_ts.dll <br />32-разрядное php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядное php7ts.dll|  
|64-разрядной php_sqlsrv_71_nts.dll<br />64-разрядной php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядной php7.dll|  
|64-разрядной php_sqlsrv_71_ts.dll <br />64-разрядной php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядной php7ts.dll|   
|32-разрядное php_sqlsrv_72_nts.dll<br />32-разрядное php_pdo_sqlsrv_72_nts.dll|7.2|нет |32-разрядное php7.dll|  
|32-разрядное php_sqlsrv_72_ts.dll <br />32-разрядное php_pdo_sqlsrv_72_ts.dll |7.2|да|32-разрядное php7ts.dll|  
|64-разрядной php_sqlsrv_72_nts.dll<br />64-разрядной php_pdo_sqlsrv_72_nts.dll|7.2|нет |64-разрядной php7.dll|  
|64-разрядной php_sqlsrv_72_ts.dll <br />64-разрядной php_pdo_sqlsrv_72_ts.dll |7.2|да|64-разрядной php7ts.dll|  

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|нет |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|да|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|нет |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|да|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|нет |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|да|

**Драйверы Microsoft 4.3 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|32-разрядное php_sqlsrv_7_nts.dll <br />32-разрядное php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядное php7.dll|
|32-разрядное php_sqlsrv_7_ts.dll  <br />32-разрядное php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядное php7ts.dll|
|64-разрядной php_sqlsrv_7_nts.dll <br />64-разрядной php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядной php7.dll|  
|64-разрядной php_sqlsrv_7_ts.dll  <br />64-разрядной php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядной php7ts.dll|
|32-разрядное php_sqlsrv_71_nts.dll<br />32-разрядное php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядное php7.dll|  
|32-разрядное php_sqlsrv_71_ts.dll <br />32-разрядное php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядное php7ts.dll|  
|64-разрядной php_sqlsrv_71_nts.dll<br />64-разрядной php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядной php7.dll|  
|64-разрядной php_sqlsrv_71_ts.dll <br />64-разрядной php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядной php7ts.dll|   

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|нет |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|да|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|нет |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|да|  

**Драйверы Microsoft 4.0 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|нет|32-разрядное php7.dll|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|да|32-разрядное php7ts.dll|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|нет|64-разрядной php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|да|64-разрядной php7ts.dll|   

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|нет |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|да|

**Драйверы Microsoft 3.2 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|нет|php5.dll|  
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|да|php5ts.dll|  

**Драйверы Microsoft 3.1 for PHP for SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  

## <a name="see-also"></a>См. также  
[Начало работы с драйверы Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по API для драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  

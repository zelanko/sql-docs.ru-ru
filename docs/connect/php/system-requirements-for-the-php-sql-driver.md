---
title: "Требования к системе для драйвера PHP SQL | Документы Microsoft"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: "93"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: abff6843dbf1b8f1362f10dbf2fe52fa5f686515
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="system-requirements-for-the-php-sql-driver"></a>Требования к системе для драйвера SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Для доступа к данным в SQL Server или база данных SQL Azure с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], необходимо установить на компьютере следующие компоненты:  
  
-   Требуется PHP. Сведения о том, как загрузить и установить актуальные и стабильные двоичные файлы см. в разделе [http://php.net](http://go.microsoft.com/fwlink/?LinkId=101876).  Драйверы Майкрософт для PHP для SQL Server требуются следующие версии:
  
|Версия драйверов Майкрософт для PHP для SQL Server|Поддерживаемые версии PHP|  
|----------------------------------------------------|--------------------------|  
|4.3|PHP 7.0 и PHP 7.1| 
|4.0|PHP 7.0|  
|3.2|PHP 5.6.4+ или<br /><br />PHP 5.5.16+ или<br /><br />PHP 5.4.32|  
|3.1|PHP 5.5.16+ или<br /><br />PHP 5.4.32|  
|3.0|PHP 5.4.32 или<br /><br />PHP 5.3.0|  
|2.0|PHP 5.3.0 или<br /><br />PHP 5.2.4 или<br /><br />PHP 5.2.13|  
  
-   Версия файла драйвера должна находиться в каталоге расширения PHP. Сведения о разных файлах драйвера см. в разделе "Версии драйвера" ниже в этой статье. Сведения о настройке драйвера для среды выполнения PHP см. в статье [Загрузка драйвера SQL PHP](../../connect/php/loading-the-php-sql-driver.md)  . Сведения о скачивании драйверов см. в статье [Драйверы Майкрософт для PHP для SQL Server](http://www.microsoft.com/download/details.aspx?id=20098).  
  
-   Требуется веб-сервер. Веб-сервер должен быть настроен на выполнение PHP. Сведения о размещении приложений PHP с помощью Internet Information Services (IIS) 6.0 см. в разделе [использование FastCGI для размещения приложений PHP в IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=117131). Сведения о размещении приложений PHP с помощью служб IIS 7.0 см. в статье [Использование FastCGI для размещения приложений PHP в службах IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=117132).  
  
    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] был протестирован в службах IIS 6 и IIS 7 с помощью FastCGI.  
  
    > [!NOTE]  
    > Корпорация Майкрософт обеспечивает поддержку только для служб IIS.  
  
-   Требуется правильная версия драйвера Microsoft ODBC для SQL Server или собственный клиент SQL Server на компьютере, где выполняется PHP.  При использовании 64-разрядной операционной системе ODBC 64-разрядный установщик устанавливает 32-разрядных и 64-разрядные драйверы ODBC. Если вы используете 32-разрядной операционной системе, используйте ODBC x86 установщика.

|Версия драйверов Майкрософт для PHP для SQL Server|Версия драйвера Microsoft ODBC для SQL Server или собственный клиент SQL Server|  
|----------------------------------------------------|--------------------------|
|4.3|Драйвер Microsoft ODBC 11 для SQL Server или Microsoft ODBC Driver 13.1 for SQL Server. Загрузить драйвер Microsoft ODBC [Microsoft ODBC Driver 11 для SQL Server страницы](http://www.microsoft.com/download/details.aspx?id=36434) или [Microsoft ODBC Driver 13.1 для сервера SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=53339)|    
|4.0|Драйвер Microsoft ODBC 11 для SQL Server или Microsoft ODBC Driver 13 for SQL Server. Загрузить драйвер Microsoft ODBC [Microsoft ODBC Driver 11 для SQL Server страницы](http://www.microsoft.com/download/details.aspx?id=36434) или [Microsoft ODBC Driver 13 для SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)|  
|3.2 или <br><br> 3.1|Драйвер Microsoft ODBC 11 для SQL Server. Загрузить драйвер Microsoft ODBC [Microsoft ODBC Driver 11 для SQL Server](http://www.microsoft.com/download/details.aspx?id=36434)|   
|3.0|Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Native Client. Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Native Client можно скачать на [странице пакета дополнительных компонентов SQL Server 2012](http://go.microsoft.com/fwlink/?LinkID=236805)| 
|2.0|Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro_md.md)] Native Client:<br /><br />[Пакет загрузки X86](http://go.microsoft.com/fwlink/?LinkID=188400&clcid=0x409) для 32-разрядных операционных систем <br /><br />[Пакет загрузки X64](http://go.microsoft.com/fwlink/?LinkID=188401&clcid=0x409) для 64-разрядных операционных систем|  

  
Если вы используете драйвер SQLSRV, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) возвращает сведения о версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Native Client или драйвер ODBC для SQL Server используется [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Если вы используете драйвер PDO_SQLSRV, можно использовать [PDO::getAttribute](../../connect/php/pdo-getattribute.md) для обнаружения версии.  



## <a name="database-versions"></a>Версии базы данных
-   Поддерживаются базы данных SQL Azure. Сведения см. в разделе [подключение к базе данных SQL Microsoft Azure](../../connect/php/connecting-to-microsoft-azure-sql-database.md). 

- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]версии 4.3 поддерживает SQL Server 2008 R2 и более поздних версий
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]поддерживаемые версии 4.0 SQL Server 2008 и более поздних версий
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]поддерживаемые версии 3.1 SQL Server 2008 и более поздних версий
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]поддержка версий 2.0 и 3.0 SQL Server 2005 и более поздних версий


## <a name="driver-versions"></a>Версии драйвера  
Этот раздел содержит драйверы, которые входят в состав каждой версии [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
Чтобы настроить драйвер для использования в среде выполнения PHP, выполните инструкции по установке в [Загрузка драйвера SQL PHP](../../connect/php/loading-the-php-sql-driver.md).  
  
**Драйверы Microsoft 4.3 для PHP для SQL Server:**  

В Windows для 4.3 следующие версии драйвера установлены:
  
|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|нет|32-разрядное php7.dll| 
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|да|32-разрядное php7ts.dll| 
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|нет|64-разрядной php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|да|64-разрядной php7ts.dll| 
|php_sqlsrv_71_nts_x86.dll<br /><br />php_pdo_sqlsrv_71_nts_x86.dll|7.1|нет|32-разрядное php7.dll|  
|php_sqlsrv_71_ts_x86.dll<br /><br />php_pdo_sqlsrv_71_ts_x86.dll|7.1|да|32-разрядное php7ts.dll|  
|php_sqlsrv_71_nts_x64.dll<br /><br />php_pdo_sqlsrv_71_nts_x64.dll|7.1|нет|64-разрядной php7.dll|  
|php_sqlsrv_71_ts_x64.dll<br /><br />php_pdo_sqlsrv_71_ts_x64.dll|7.1|да|64-разрядной php7ts.dll|   
  
**Драйверы Microsoft 4.0 для PHP для SQL Server:**  

В Windows для версии 4.0 следующие версии драйвера установлены:
  
|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|нет|32-разрядное php7.dll|  
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|да|32-разрядное php7ts.dll|  
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|нет|64-разрядной php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|да|64-разрядной php7ts.dll|   
  
В поддерживаемых версий Linux соответствующую версию sqlsrv и/или pdo_sqlsrv можно установить с помощью PHP нагрузка PECL пакета системы. 
  
**Драйверы 3.2 Майкрософт для PHP для SQL Server устанавливают следующие версии драйвера:**  
  
|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br /><br />php_pdo_sqlsrv_56_nts.dll|5.6|нет|php5.dll|  
|php_sqlsrv_56_ts.dll<br /><br />php_pdo_sqlsrv_56_ts.dll|5.6|да|php5ts.dll|  
  
**Microsoft Drivers 3.1 for PHP for SQL Server устанавливает следующие версии драйвера:**  
  
|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  
  
**Microsoft Drivers 3.0 for PHP for SQL Server устанавливает следующие версии драйвера:**  
  
|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts.dll<br /><br />php_pdo_sqlsrv_53_nts.dll|5.3|нет|php5.dll|  
|php_sqlsrv_53_ts.dll<br /><br />php_pdo_sqlsrv_53_ts.dll|5.3|да|php5ts.dll|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
  
**Microsoft Drivers 2.0 for PHP for SQL Server устанавливает следующие версии драйвера:**  
  
|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts_vc6.dll<br /><br />php_pdo_sqlsrv_53_nts_vc6.dll|5.3|нет|php5.dll|  
|php_sqlsrv_53_nts_vc9.dll<br /><br />php_pdo_sqlsrv_53_nts_vc9.dll|5.3|нет|php5.dll|  
|php_sqlsrv_53_ts_vc6.dll<br /><br />php_pdo_sqlsrv_53_ts_vc6.dll|5.3|да|php5ts.dll|  
|php_sqlsrv_53_ts_vc9.dll<br /><br />php_pdo_sqlsrv_53_ts_vc9.dll|5.3|да|php5ts.dll|  
|php_sqlsrv_52_nts_vc6.dll<br /><br />php_pdo_sqlsrv_52_nts_vc6.dll|5.2|нет|php5.dll|  
|php_sqlsrv_52_ts_vc6.dll<br /><br />php_pdo_sqlsrv_52_ts_vc6.dll|5.2|да|php5ts.dll|  
  
Если имя файла драйвера содержит "vc9", его следует использовать с версией PHP, скомпилированной с помощью Visual C++ 9.0.  
## <a name="operating-systems"></a>Операционные системы 
Ниже приведены поддерживаемые операционные системы для версии драйвера:

-   4.3:
    -   Windows Server 2012  
    -   Windows Server 2012 R2
    -   Windows Server 2016 
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10
    -   Ubuntu 15.10 (64-разрядная версия)
    -   Ubuntu 16.04 (64-разрядная версия)
    -   Debian 8 (64-разрядная версия)
    -   Red Hat Enterprise Linux 7 (64-разрядная версия)
    -   Mac OS Сьерра (64-разрядная версия)
    -   Mac OS El Capitan (64-разрядная версия)
    
-   4.0:  
    -   Windows Server 2008 с пакетом обновления 2 (SP2)
    -   Windows Server 2008 R2 с пакетом обновления 1 (SP1)  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows Vista с пакетом обновления 2 (SP2)  
    -   Windows 7 с пакетом обновления 1 (SP1)  
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10 
    -   Ubuntu 15.04 (64-разрядная версия)
    -   Ubuntu 16.04 (64-разрядная версия)
    -   Red Hat Enterprise Linux 7 (64-разрядная версия)

 
-   3.2 и 3.1:  
    -   Windows Server 2008 R2 с пакетом обновления 1 (SP1)  
    -   Windows Vista с пакетом обновления 2 (SP2)  
    -   Windows Server 2008 с пакетом обновления 2 (SP2)  
    -   Windows 7 с пакетом обновления 1 (SP1)  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows 8  
    -   Windows 8.1  
  
  
-   3.0:  
    -   Windows Server 2008 R2 с пакетом обновления 1 (SP1)  
    -   Windows Vista с пакетом обновления 2 (SP2)  
    -   Windows Server 2008 с пакетом обновления 2 (SP2)  
    -   Windows 7 с пакетом обновления 1 (SP1)  


-   2.0:
    -   [!INCLUDE[winxpsvr](../../includes/winxpsvr_md.md)] с пакетом обновления 1 (SP1)  
    -   Windows XP с пакетом обновления 3 (SP3)  
    -   Windows Vista с пакетом обновления 1 (SP1) или более поздней версии  
    -   Windows Server 2008  
    -   Windows Server 2008 R2  
    -   Windows 7  
  
## <a name="see-also"></a>См. также:  
[Приступая к работе с драйвером SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md)
[Руководство по программированию для драйвера SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  

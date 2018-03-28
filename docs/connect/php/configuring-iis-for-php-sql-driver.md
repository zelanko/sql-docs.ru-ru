---
title: Настройка IIS для драйверов Майкрософт для PHP для SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, Internet Information Services
ms.assetid: d2dc75d3-9bf7-481c-85f2-8b6310b21461
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a6d655f379963362779cb90a4f5090aa239adea4
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="configuring-iis-for-the-microsoft-drivers-for-php-for-sql-server"></a>Настройка IIS для драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Этот раздел содержит ссылки на ресурсы на [веб-сайта Internet Information Services (IIS)](https://www.iis.net/) , посвященные настройке служб IIS для размещения приложений PHP. Перечисленные здесь ресурсы относятся к использованию протокола FastCGI со службами IIS. FastCGI является стандартным протоколом, который позволяет исполняемым файлам CGI исполняющей среды взаимодействовать с веб-сервером. Протокол FastCGI отличается от стандартного протокола CGI тем, что FastCGI повторно использует процессы CGI для нескольких запросов.  
  
## <a name="tutorials"></a>Учебники  
Ниже представлены ссылки на руководства по настройке протокола FastCGI для PHP и размещению приложений PHP в службах IIS 6.0 и IIS 7.0:  
  
-   [FastCGI с PHP](https://docs.microsoft.com/iis/web-hosting/web-server-for-shared-hosting/fastcgi-with-php)  
-   [Использование FastCGI для размещения приложений PHP в IIS 7.0](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-applications-on-iis/using-fastcgi-to-host-php-applications-on-iis)  
-   [Использование FastCGI для размещения приложений PHP в службах IIS 6.0](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-applications-on-iis/using-fastcgi-to-host-php-applications-on-iis-60)  
-   [Настройка расширения FastCGI для IIS 6.0](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-on-iis/configuring-the-fastcgi-extension-for-iis-60)  
  
## <a name="video-presentations"></a>Видеопрезентации  
Ниже представлены ссылки на видеопрезентации о настройке FastCGI для PHP и использовании функций служб IIS 7.0 для размещения приложений PHP:  
  
-   [Настройка FastCGI для PHP](https://docs.microsoft.com/en-us/iis/application-frameworks/running-php-applications-on-iis/set-up-fastcgi-for-php)  
-   [Использование PHP в службах Microsoft IIS 7](https://docs.microsoft.com/en-us/iis/application-frameworks/running-php-applications-on-iis/mix08-partying-with-php-on-microsoft-internet-information-services-7-and-above)  
  
## <a name="support-resources"></a>Ресурсы поддержки  
Указанные ниже форумы предоставляют поддержку сообщества по использованию FastCGI в службах IIS:  
  
-   [FastCGI Handler](https://forums.iis.net/1103.aspx)  
-   [Службы IIS 7 — модуль FastCGI](https://forums.iis.net/1104.aspx)  
  
## <a name="see-also"></a>См. также  
[Начало работы с драйверы Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  

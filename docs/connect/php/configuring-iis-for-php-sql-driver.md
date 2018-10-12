---
title: Настройка служб IIS для драйверов Майкрософт на языке PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- configuring, Internet Information Services
ms.assetid: d2dc75d3-9bf7-481c-85f2-8b6310b21461
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b550fb7300ffdb2d37ae4407aaeeb43a49c89f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654782"
---
# <a name="configuring-iis-for-the-microsoft-drivers-for-php-for-sql-server"></a>Настройка служб IIS для драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья содержит ссылки на ресурсы на [веб-сайте служб IIS](https://www.iis.net/), посвященные настройке служб IIS для размещения приложений PHP. Перечисленные здесь ресурсы относятся к использованию протокола FastCGI со службами IIS. FastCGI является стандартным протоколом, который позволяет исполняемым файлам CGI исполняющей среды взаимодействовать с веб-сервером. Протокол FastCGI отличается от стандартного протокола CGI тем, что FastCGI повторно использует процессы CGI для нескольких запросов.  
  
## <a name="tutorials"></a>Учебники  
Ниже представлены ссылки на руководства по настройке протокола FastCGI для PHP и размещению приложений PHP в службах IIS 6.0 и IIS 7.0:  
  
-   [FastCGI с PHP](https://docs.microsoft.com/iis/web-hosting/web-server-for-shared-hosting/fastcgi-with-php)  
-   [Использование FastCGI для размещения приложений PHP в службах IIS 7.0](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-applications-on-iis/using-fastcgi-to-host-php-applications-on-iis)  
-   [Использование FastCGI для размещения приложений PHP в службах IIS 6.0](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-applications-on-iis/using-fastcgi-to-host-php-applications-on-iis-60)  
-   [Настройка расширения FastCGI для служб IIS 6.0](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-on-iis/configuring-the-fastcgi-extension-for-iis-60)  
  
## <a name="video-presentations"></a>Видеопрезентации  
Ниже представлены ссылки на видеопрезентации о настройке FastCGI для PHP и использовании функций служб IIS 7.0 для размещения приложений PHP:  
  
-   [Настройка FastCGI для PHP](https://docs.microsoft.com/iis/application-frameworks/running-php-applications-on-iis/set-up-fastcgi-for-php)  
-   [Использование PHP в службах Microsoft IIS 7](https://docs.microsoft.com/iis/application-frameworks/running-php-applications-on-iis/mix08-partying-with-php-on-microsoft-internet-information-services-7-and-above)  
  
## <a name="support-resources"></a>Ресурсы поддержки  
Указанные ниже форумы предоставляют поддержку сообщества по использованию FastCGI в службах IIS:  
  
-   [Обработчик FastCGI](https://forums.iis.net/1103.aspx)  
-   [Службы IIS 7 — модуль FastCGI](https://forums.iis.net/1104.aspx)  
  
## <a name="see-also"></a>См. также:  
[Приступая к работе с драйверами Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  

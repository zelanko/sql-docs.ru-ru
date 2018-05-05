---
title: Общие сведения о драйверы Майкрософт для PHP для SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66559249-34c0-409d-b919-9b5bf0c4c9ec
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c44d3278a61f8df573c909a48507624c563df64b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-the-microsoft-drivers-for-php-for-sql-server"></a>Общие сведения о драйверы Майкрософт для PHP для SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Представляет собой расширение PHP, который предоставляет доступ к данным для SQL Server 2005 и более поздних версиях, включая базы данных SQL Azure. Данное расширение предоставляет процедурный интерфейс с помощью драйвера SQLSRV и объектно ориентированный интерфейс, с помощью драйвера PDO_SQLSRV для доступа к данным во всех версиях SQL Server, включая Express, начиная с SQL Server 2005. Поддержка версии 3.1 и более поздних версий драйверы начинается с SQL Server 2008. API [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддерживает проверку подлинности Windows, транзакции, привязку параметров, потоковую передачу, доступ к метаданным и обработку ошибок.  
  
Чтобы использовать [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], должен иметь правильную версию собственного клиента SQL Server или работает под управлением Microsoft ODBC Driver установлен на том же компьютере PHP.  Дополнительные сведения см. в разделе [требования к системе для драйвера Microsoft SQL Server для PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|---------|---------------|  
| ![Загрузка стрелка вниз обведен](../../ssdt/media/download.png)[выполнять загрузку драйверов для PHP для SQL Server](download-drivers-php-sql-server.md) | Ссылки для загрузки драйверы Майкрософт для PHP для SQL Server. |
|[Заметки о выпуске для драйверов Майкрософт для PHP для SQL Server](../../connect/php/release-notes-for-the-php-sql-driver.md)|Список возможностей, которые были добавлены в версии 4.0, 3.2, 3.1, 3.0 и 2.0.|  
|[Ресурсы поддержки драйверы Майкрософт для PHP для SQL Server](../../connect/php/support-resources-for-the-php-sql-driver.md)|Содержит ссылки на ресурсы, которые могут оказаться полезными при разработке приложений, использующих [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].|  
|[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)|Содержит информацию, которая может оказаться полезной при запуске примеров кода, приведенных в этой документации.|  
  
## <a name="reference"></a>Справочник  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  
## <a name="see-also"></a>См. также  
[Начало работы с драйверы Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)

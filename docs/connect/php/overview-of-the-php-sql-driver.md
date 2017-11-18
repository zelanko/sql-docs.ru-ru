---
title: "Общие сведения о драйвере PHP SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66559249-34c0-409d-b919-9b5bf0c4c9ec
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4badc426f6dbff44784bd8487b04bc0665d959ad
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="overview-of-the-php-sql-driver"></a>Общие сведения о драйвере SQL PHP

![Загрузка стрелка вниз обведен](../../ssdt/media/download.png)[для загрузки драйвера PHP для SQL Server](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Представляет собой расширение PHP, который предоставляет доступ к данным для SQL Server 2005 и более поздних версиях, включая базы данных SQL Azure. Данное расширение предоставляет процедурный интерфейс (драйвер SQLSRV) и объектно ориентированный интерфейс (драйвер PDO_SQLSRV) для доступа к данным во всех версиях (включая экспресс-выпуск) начиная с SQL Server 2005 (поддержка для PHP для SQL Server версии 3.1 и более поздние версии начинается с SQL Server 2008). API [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддерживает проверку подлинности Windows, транзакции, привязку параметров, потоковую передачу, доступ к метаданным и обработку ошибок.  
  
Для использования [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] должен иметь правильную версию собственного клиента SQL Server или Microsoft ODBC Driver установлен на том же компьютере PHP выполняется.  Подробные сведения см. в статье [Требования к системе для драйвера SQL PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|---------|---------------|  
| ![Загрузка стрелка вниз обведен](../../ssdt/media/download.png)[для загрузки драйвера PHP для SQL Server](../sql-connection-libraries.md#anchor-20-drivers-relational-access) | Ссылки для скачивания исходного кода и драйверов Microsoft PHP Driver for SQL Server. |
|[Заметки о выпуске для драйвера SQL PHP](../../connect/php/release-notes-for-the-php-sql-driver.md)|Список возможностей, которые были добавлены в версии 4.0, 3.2, 3.1, 3.0 и 2.0.|  
|[Ресурсы поддержки для драйвера SQL PHP](../../connect/php/support-resources-for-the-php-sql-driver.md)|Содержит ссылки на ресурсы, которые могут оказаться полезными при разработке приложений, использующих [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].|  
|[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)|Содержит информацию, которая может оказаться полезной при запуске примеров кода, приведенных в этой документации.|  
  
## <a name="reference"></a>Справочник  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
[Приступая к работе с драйвером PHP SQL](../../connect/php/getting-started-with-the-php-sql-driver.md)
[руководство по программированию для драйвера PHP SQL](../../connect/php/programming-guide-for-php-sql-driver.md)
[пример приложения &#40; Драйвер SQLSRV &#41;](../../connect/php/example-application-sqlsrv-driver.md)


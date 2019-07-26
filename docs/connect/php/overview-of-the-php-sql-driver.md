---
title: Обзор драйверов Майкрософт для PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 66559249-34c0-409d-b919-9b5bf0c4c9ec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 25519d06df8b948d5cfc5d387029cf09beafc856
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936276"
---
# <a name="overview-of-the-microsoft-drivers-for-php-for-sql-server"></a>Обзор драйверов Майкрософт для PHP для SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] — это расширение PHP, предоставляющее доступ к данным для SQL Server 2005 и более поздних версий, включая базу данных SQL Azure. Расширение предоставляет процедурный интерфейс с драйвером SQLSRV и объектно-ориентированный интерфейс с драйвером PDO_SQLSRV для доступа к данным во всех версиях SQL Server, включая Express, начиная с SQL Server 2005. Поддержка версии 3,1 и более поздних версий драйверов начинается с SQL Server 2008. API [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддерживает проверку подлинности Windows, транзакции, привязку параметров, потоковую передачу, доступ к метаданным и обработку ошибок.  
  
Для использования [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]необходимо иметь правильную версию SQL Server Native Client или драйвер Microsoft ODBC, установленный на том же компьютере PHP.  Дополнительные сведения см. [в разделе Требования к системе для драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|---------|---------------|  
| ![Скачать-стрелка вниз-в круге](../../ssdt/media/download.png)[, чтобы скачать драйверы для PHP для SQL Server](download-drivers-php-sql-server.md) | Ссылки на загрузку драйверов Майкрософт для PHP для SQL Server. |
|[Заметки о выпуске драйверов Майкрософт для PHP для SQL Server](../../connect/php/release-notes-php-sql-driver.md)|Содержит список функций, которые были добавлены для версий 4.0, 3.2, 3.1, 3.0 и 2.0.|  
|[Ресурсы поддержки по драйверам Майкрософт для PHP для SQL Server](../../connect/php/support-resources-for-the-php-sql-driver.md)|Содержит ссылки на ресурсы, которые могут оказаться полезными при разработке приложений, использующих [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].|  
|[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)|Содержит информацию, которая может оказаться полезной при запуске примеров кода, приведенных в этой документации.|  
| &nbsp; | &nbsp; |

## <a name="reference"></a>Справочник

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  

## <a name="see-also"></a>См. также:

[Getting Started with the Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md) (Начало работы с драйверами Майкрософт для PHP для SQL Server)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)

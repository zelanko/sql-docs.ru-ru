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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c8f5cbf011165b41b353a37d8973031f55c2db6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922816"
---
# <a name="overview-of-the-microsoft-drivers-for-php-for-sql-server"></a>Обзор драйверов Майкрософт для PHP для SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] — это расширение PHP, предоставляющее доступ к данным для SQL Server 2005 и более поздних версий, включая базу данных SQL Azure. Данное расширение предоставляет процедурный интерфейс для драйвера SQLSRV и объектно-ориентированный интерфейс для драйвера PDO_SQLSRV, позволяющие обращаться к данным в любой версии SQL Server, начиная с SQL Server 2005 (включая экспресс-выпуск). Поддержка драйверов версии 3.1 и более поздних версий начинается с SQL Server 2008. API [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддерживает проверку подлинности Windows, транзакции, привязку параметров, потоковую передачу, доступ к метаданным и обработку ошибок.  
  
Чтобы использовать [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], на том же компьютере, где выполняется PHP, должна быть установлена правильная версия SQL Server Native Client или драйвера Майкрософт для ODBC.  Дополнительные сведения см. в статье [Системные требования драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|---------|---------------|  
| ![Стрелка вниз в кружочке как обозначение скачивания](../../ssms/media/download-icon.png)[Скачивание драйверов PHP для SQL Server](download-drivers-php-sql-server.md) | Ссылки на загрузку драйверов Майкрософт для PHP для SQL Server. |
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

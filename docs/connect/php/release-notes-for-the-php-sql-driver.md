---
title: Заметки о выпуске драйверов Майкрософт для PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0c2e7377b1072c30e5c5ef038b93a88f0c222260
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744354"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Заметки о выпуске драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

На этой странице описаны, что был добавлен в каждую версию [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

## <a name="whats-new-in-version-56"></a>Новые возможности версии 5.6

- Поддержка PHP 7.3
- Поддержка Microsoft ODBC Driver 17.3 на всех платформах
- Поддержка macOS Mojave (требует ODBC драйвер 17.3 или более поздней версии)
- Поддержка Ubuntu 18.10 и Suse Linux 15 (оба требуют ODBC драйвер 17.3 или более поздней версии)
- Прекращена поддержка PHP 7.0
- Прекращена поддержка Linux Ubuntu 17.10 и macOS El Capitan
- Поддержка маркера доступа Azure AD (в Linux и macOS требуется драйвер ODBC 17.2 + и unixODBC 2.3.6+)
- Поддержка проверки подлинности с помощью Azure AD, с помощью управляемого удостоверения для ресурсов Azure (требуется драйвер ODBC 17.3 +)
- Новые функции выборки:
  - Новый флаг PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE для pdo_sqlsrv для возврата даты и времени в виде объектов
  - Добавьте параметр ReturnDatesAsStrings на уровне инструкций для sqlsrv
  - Новые параметры на уровне соединения и инструкции для обоих драйверов для форматирования десятичные значения в выбранных результатов
- Поддержка статическую компиляцию драйверы, если пользователи решили сборку из исходного файла
- Повышена производительности за счет кэширования метаданных при выборке и ускоряя преобразования строк Юникода

## <a name="whats-new-in-version-53"></a>Новые возможности версии 5.3

- Поддержка Microsoft ODBC Driver 17.2 на всех платформах
- Поддержка macOS High Sierra (требует ODBC Driver 17 и более поздних версий)
- Поддержки для хранилища ключей Azure для постоянного шифрования для основных CRUD функциональные возможности таких что функция Always Encrypted доступна для всех поддерживаемых платформ Windows, Linux или macOS [использование функции Always Encrypted с драйверами PHP для SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
- Поддержка Ubuntu LTS 18.04 (требуется 17.2 драйвера ODBC)
- Поддержка устойчивость подключения в Linux или macOS также (требуется 17.2 драйвера ODBC)

## <a name="whats-new-in-version-52"></a>Новые возможности версии 5.2

- Поддержка PHP 7.2.1 и на Windows и 7.2.0 и на других платформах
- Поддержка Microsoft ODBC Driver 17
  - Версия 17 теперь используется по умолчанию на всех платформах
- Поддержка Ubuntu 17.10, Debian 9 и Suse Enterprise Linux 12
- Прекращена поддержка Ubuntu 15.10
- Поддержка Always Encrypted с CRUD дополнительные функции Windows. Дополнительные сведения см. в разделе [использование функции Always Encrypted с драйверами PHP для SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
  - Поддержка Windows Certificate Store
  - Постоянное шифрование поддерживается только с Microsoft ODBC Driver 17 и выше
- Поддержка национальных настроек не UTF8 в Linux и macOS
  - Языковые стандарты Non-UTF8 в Linux и macOS поддерживаются только с Microsoft ODBC Driver 17 и выше
- Поддержка хранилища данных SQL Azure
- Поддержка управляемый экземпляр Azure SQL (расширенная закрытая Предварительная версия)


## <a name="whats-new-in-version-43"></a>Новые возможности версии 4.3

- Поддержка PHP 7.1
- Поддержка macOS Sierra и macOS El Capitan
- Поддержка Ubuntu 15.10 и Debian 8
- Прекращена поддержка Ubuntu 15.04
- Поддержка групп доступности AlwaysOn с помощью разрешение IP-адресов прозрачной сети. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).
- Добавлена поддержка для типа данных sql_variant с ограничением.
- Поддержка простоя устойчивость подключения в Windows. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).
- Поддержка для Linux и macOS организации пулов соединений. Дополнительные сведения см. в статье [Организация пулов соединений](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Поддержка проверки подлинности Azure Active Directory с ActiveDirectoryPassword и SqlPassword. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Новые возможности версии 4.0

- Поддержка PHP 7.0  
- Поддержка 64-разрядных
- Поддержка Ubuntu 15.04, Ubuntu 16.04 и RedHat 7

## <a name="whats-new-in-version-32"></a>Новые возможности версии 3.2

- Поддержка PHP 5.6.   
- Содержит последние обновления для предыдущих версий PHP 5.5 и 5.4.   
- Требуется драйвер Microsoft ODBC Driver 11 для SQL Server  

## <a name="whats-new-in-version-31"></a>Новые возможности версии 3.1

- Поддержка PHP 5.5.  
- Требуется драйвер Microsoft ODBC Driver 11 для SQL Server. Предыдущие версии требуют наличия SQL Native Client.  

## <a name="whats-new-in-version-30"></a>Новые возможности версии 3.0  

- Поддержка PHP 5.4.  PHP 5.2 не поддерживается в версии 3 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
- Добавлен параметр подключения AttachDBFileName. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).  
- Поддержка LocalDB, которая была добавлена в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Дополнительные сведения см. в разделе [поддержка LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Добавлен параметр подключения AttachDBFileName. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).  
- Поддержка функций высокой доступности и аварийного восстановления. Дополнительные сведения см. в разделе [Поддержка высокой доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Поддержка клиентских курсоров (кэширования результирующего набора в памяти). Дополнительные сведения см. в статьях [Типы курсоров &#40;драйвер SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) и [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Был добавлен атрибут PDO::ATTR_EMULATE_PREPARE. Подробнее см. в разделе [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Новые возможности версии 2.0  
В версии 2.0 была добавлена поддержка драйвера PDO_SQLSRV. Дополнительные сведения см. в статье [Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a>См. также:  
[Обзор драйверов Майкрософт для PHP для SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)

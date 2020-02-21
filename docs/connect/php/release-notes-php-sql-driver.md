---
title: Заметки о выпуске драйверов Майкрософт для PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: v-dapugl, kenvh
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5e279ba446e790a2262e5f0effe160632065dcba
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76941211"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Заметки о выпуске драйверов Майкрософт для PHP для SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

На этой странице описывается, что было добавлено в каждой версии [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

<!--
Hello, We are standardizing the format of content inside our Release Notes (or What's New) articles.
Instead of bullets (or paragraphs), we have shifted to the 2-column format you see for H2 **What's New in Version 5.6**.
It is not necessary to reformat all the older H2 sections in this Release Notes file, but.....

Going forward, please be sure to use the 2-column format.

Also, all Release Notes .md file names now must begin with 'release-notes-*.md'.  And no filler words.
The 5.6 edition of this file is being renamed.....
FROM:  'release-notes-for-the-php-sql-driver.md'
TO  :  'release-notes-php-sql-driver.md'

For any questions, ask GeneMi or CraigG.
Thanks a lot.  2019-03-28  (DevO= 1467988)
-->

## <a name="whats-new-in-version-58"></a>Новые возможности версии 5.8

| Изменения | Сведения |
| :------- | :------ |
| Добавлена поддержка PHP 7.4. | &nbsp; |
| Прекращена поддержка PHP 7.1. | &nbsp; |
| Добавлена поддержка драйвера Microsoft ODBC Driver 17.5 на всех платформах. | &nbsp; |
| Добавлена поддержка Debian 10 и Red Hat 8. | Для обоих требуется драйвер ODBC 17.4 или более поздней версии. |
| Добавлена поддержка macOS Catalina, Alpine Linux 3.11<sup>1</sup> и Ubuntu 19.10. | Для всех систем требуется драйвер ODBC 17.5 или более поздней версии. |
| Прекращена поддержка SQL Server 2008 R2, macOS Sierra, Ubuntu 18.10 и Ubuntu 19.04. | &nbsp; |
| Поддержка параметра языка при подключении к SQL Server. | &nbsp; |
| Поддержка типов расширенных строк PHP, представленных в PHP 7.2. | &nbsp; |
| Поддержка получения метаданных чувствительности классификации данных. | Требуются SQL Server 2019 и драйвер ODBC 17.4.2 или более поздней версии. |
| Поддержка функции Always Encrypted с безопасными анклавами. | Требуется драйвер ODBC 17.4 или более поздней версии. |
| Поддержка настраиваемых параметров языковых стандартов в Linux и macOS. |
| Повышение производительности за счет кэширования метаданных при выборке и пропуска избыточных вызовов. | &nbsp; |
| &nbsp; | &nbsp; |

<sup>1</sup> Поддержка Alpine Linux является экспериментальной для версии 5.8.

## <a name="whats-new-in-version-56"></a>Новые возможности версии 5.6

| Изменения | Сведения |
| :------- | :------ |
| Поддержка PHP 7.3. | &nbsp; |
| Прекращена поддержка PHP 7.0. | &nbsp; |
| Поддержка драйвера Microsoft ODBC Driver 17.3 на всех платформах. | &nbsp; |
| Поддержка macOS Mojave. | Требуется драйвер ODBC 17.3 или более поздней версии. |
| Поддержка Ubuntu 18.10 и SUSE Linux 15. | Для обоих требуется драйвер ODBC 17.3 или более поздней версии. |
| Прекращена поддержка Linux Ubuntu 17.10 и macOS El Capitan. | &nbsp; |
| Поддержка маркера доступа AAD. | В Linux и macOS требуются драйвер ODBC 17.2+ и unixODBC 2.3.6+. |
| Поддержка проверки подлинности в AAD с помощью управляемого удостоверения для ресурсов Azure. | Требуется драйвер ODBC 17.3+. |
| Новые функции выборки | &bull; &nbsp; Добавлен новый флаг PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE для pdo_sqlsrv, позволяющий возвращать элементы даты и времени в качестве объектов.<br/><br/>&bull; &nbsp; Добавлен параметр ReturnDatesAsStrings на уровень инструкции для sqlsrv.<br/><br/>&bull; &nbsp; Добавлены новые параметры на уровнях подключения и инструкции для обоих драйверов, позволяющие форматировать десятичные значения в результатах выборки. |
| Поддержка статической компиляции драйверов, если пользователь выбирает сборку из источника. | &nbsp; |
| Повышение производительности за счет кэширования метаданных при выборке и повышения скорости преобразования строк Юникода. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>Новые возможности версии 5.3

- Поддержка драйвера Microsoft ODBC Driver 17.2 на всех платформах.
- Поддержка macOS High Sierra (требуется драйвер ODBC 17 и более поздние версии).
- Поддержка Azure Key Vault для Always Encrypted для базовых функций CRUD, чтобы функция Always Encrypted была доступна для всех поддерживаемых платформ Windows, Linux или macOS. Дополнительные сведения см. в статье [Using Always Encrypted with the PHP Drivers for SQL Server](../../connect/php/using-always-encrypted-php-drivers.md) (Использование функции Always Encrypted с драйверами PHP для SQL Server).
- Поддержка Ubuntu 18.04 LTS (требуется драйвер ODBC 17.2).
- Поддержка устойчивости подключений в Linux или macOS (требуется драйвер ODBC 17.2).

## <a name="whats-new-in-version-52"></a>Новые возможности версии 5.2

- Поддержка PHP 7.2.1 и более поздних версий в Windows, а также 7.2.0 и более поздних версий на других платформах.
- Поддержка драйвера Microsoft ODBC 17.
  - Версия 17 теперь используется по умолчанию на всех платформах.
- Поддержка Ubuntu 17.10, Debian 9 и SUSE Enterprise Linux 12.
- Прекращена поддержка Ubuntu 15.10.
- Поддержка Always Encrypted с функциями CRUD в Windows. См. подробнее об [использовании функции Always Encrypted с драйвером PHP для SQL Server](../../connect/php/using-always-encrypted-php-drivers.md).
  - Поддержка хранилища сертификатов Windows.
  - Always Encrypted поддерживается только с драйвером Microsoft ODBC Driver 17 и более поздних версий.
- Поддержка языковых стандартов, отличных от UTF8, в Linux и macOS.
  - Языковые стандарты, отличные от UTF8, в Linux и macOS поддерживаются только с драйвером Microsoft ODBC Driver 17 и более поздней версии.
- Поддержка хранилища данных SQL Azure
- Поддержка Управляемого экземпляра SQL Azure.

## <a name="whats-new-in-version-43"></a>Новые возможности версии 4.3

- Поддержка PHP 7.1
- Поддержка macOS Sierra и macOS El Capitan.
- Поддержка Ubuntu 15.10 и Debian 8.
- Прекращена поддержка Ubuntu 15.04.
- Поддержка групп доступности Always On с помощью разрешения IP-адресов прозрачной сети. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).
- Добавлена поддержка типа данных sql_variant с ограничением.
- Поддержка устойчивости подключения в режиме ожидания в Windows. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).
- Поддержка организации пулов подключений для Linux и macOS. Дополнительные сведения см. в статье [Организация пулов соединений](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Поддержка проверки подлинности Azure Active Directory с помощью ActiveDirectoryPassword и SqlPassword. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Новые возможности версии 4.0

- Поддержка PHP 7.0  
- Полная поддержка 64-разрядных версий.
- Поддержка Ubuntu 15.04, Ubuntu 16.04 и RedHat 7.

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
- Поддержка LocalDB, которая была добавлена в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Дополнительные сведения о поддержке LocalDB см. в [этой статье](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Добавлен параметр подключения AttachDBFileName. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md).  
- Поддержка функций высокой доступности и аварийного восстановления. См.подробнее о [поддержке высокой доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Поддержка клиентских курсоров (кэширования результирующего набора в памяти). Дополнительные сведения см. в статьях [Типы курсоров &#40;драйвер SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) и [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Был добавлен атрибут PDO::ATTR_EMULATE_PREPARE. Подробнее см. в разделе [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Новые возможности версии 2.0

В версии 2.0 была добавлена поддержка драйвера PDO_SQLSRV. Дополнительные сведения см. в статье [Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a>См. также:

[Обзор драйверов Майкрософт для PHP для SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)

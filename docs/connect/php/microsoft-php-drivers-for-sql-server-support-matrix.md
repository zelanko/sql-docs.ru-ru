---
title: Матрица поддержки драйверы Майкрософт для PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 07/20/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: ''
ms.openlocfilehash: 82a8576365889d02381e3b18b622fd541b5b9235
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728702"
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>Драйверы Microsoft PHP для SQL Server Support Matrix
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

  В этой статье приведены матрица и политика жизненного цикла поддержки для драйвера Microsoft PHP Driver for SQL Server.

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Таблица жизненного цикла поддержки драйверы Microsoft PHP и политика
 Политика жизненного цикла поддержки Майкрософт (MSL) предоставляет понятную и предсказуемую информацию о жизненном цикле поддержки продуктов Майкрософт. Основная фаза поддержки драйверов PHP версий 3.x, 4.x и 5.x длится пять лет с даты выпуска соответствующей версии. Основная фаза поддержки определена на [веб-сайте жизненного цикла поддержки Майкрософт](https://support.microsoft.com/lifecycle).

 Возможность расширенной или настраиваемой поддержки драйвера PHP не предусмотрена.

 Перечисленные ниже версии драйверов Microsoft PHP будут поддерживаться до указанной даты окончания поддержки.

|Имя драйвера|Версия пакета драйвера|Заканчивается Основная фаза поддержки|
|-|-|-|
|Драйверы Microsoft PHP 5.3 для SQL Server|5.3|20 июля 2023 г.|
|Драйверы Microsoft PHP 5.2 для SQL Server|5.2|9 февраля 2023 г.|
|Драйверы Microsoft PHP 4.3 для SQL Server|4.3|6 июля 2022|
|Драйверы Microsoft PHP 4.0 для SQL Server|4.0|11 июля 2021|
|Драйверы Microsoft PHP 3.2 для SQL Server|3.2|9 марта 2020 г.|
|Драйверы Microsoft PHP 3.1 для SQL Server|3.1|12 декабря 2019 г.|

 Следующие драйверы Microsoft PHP больше не поддерживаются.

|Имя драйвера|Версия пакета драйвера|Заканчивается Основная фаза поддержки|
|-|-|-|
|Драйверы Microsoft PHP 3.0 для SQL Server|3.0|6 марта 2017 г.|
|Драйверы Microsoft PHP 2.0 для SQL Server|2.0|10 августа 2015 г.|
|Драйверы Microsoft PHP 1.0 для SQL Server|1.0|28 апреля 2014 г.|

## <a name="sql-server-version-certified-compatibility"></a>Сертифицированные совместимости версии SQL Server
 Приведенной ниже таблице перечислены версии SQL Server, были протестированы и сертификацию на совместимость с соответствующей версией драйвера. Мы стремимся поддерживать обратную совместимость с предыдущими версиями драйвера, но только последний поддерживаемый драйвер является проверены и сертифицированы в новых версиях SQL Server, выпуска SQL Server.

|PHP для SQL Server версии драйвера&#8594;<br />&#8595; версия SQL Server|5.3 и 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Управляемый экземпляр SQL Azure<br/> (Расширенная закрытая Предварительная версия)|Да|Да| | | | | |
|Хранилище данных SQL Azure|Да|Да| | | | | |
|SQL Server 2017   |Да|Да| | | | | |
|SQL Server 2016   |Да|Да|Да| | | | |
|SQL Server 2014   |Да|Да|Да|Да|Да| | |
|SQL Server 2012   |Да|Да|Да|Да|Да|Да| |
|SQL Server 2008 R2|Да|Да|Да|Да|Да|Да|Да|
|SQL Server 2008   | | |Да|Да|Да|Да|Да|

## <a name="php-version-support"></a>Поддерживаемые версии PHP
 Список версий драйвера Microsoft PHP поддерживаются следующие версии PHP:

|PHP для SQL Server версии драйвера&#8594;<br />&#8595; версия PHP|5.3 и 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|7.2|7.2.1+ на платформе Windows<br/>7.2.0+ на других платформах| | | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |        |        |
|5.6|       |       |       |5.6.4+  |        |        |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |        |        |
|5.4|       |       |       |5.4.32  |5.4.32  |5.4.32  |        |
|5.3|       |       |       |        |        |5.3.0   |5.3.0   |
|5.2|       |       |       |        |        |        |5.2.4<br />5.2.13|

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы
 Список версий драйвера Microsoft PHP поддерживаются следующие версии операционной системы Windows:

|PHP для SQL Server версии драйвера&#8594;<br />&#8595; операционная система|5.3 и 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Windows Server 2016                 |Да  |Да  |   |   |   |   |   |
|Windows Server 2012 R2              |Да  |Да  |Да  |Да  |Да  |   |   |
|Windows Server 2012                 |Да  |Да  |Да  |Да  |Да  |   |   |
|Windows Server 2008 R2 с пакетом обновления 1 (SP1)          |   |   |Да  |Да  |Да  |Да  |   |
|Windows Server 2008 R2              |   |   |   |   |   |   |Да  |
|Windows Server 2008 с пакетом обновления 2 (SP2)             |   |   |Да  |Да  |Да  |Да  |   |
|Windows Server 2008                 |   |   |   |   |   |   |Да  |
|Windows Server 2003 с пакетом обновления 1 (SP1)             |   |   |   |   |   |   |Да  |
|Windows 10                          |Да  |Да  |Да  |   |   |   |   |
|Windows 8.1                         |Да  |Да  |Да  |Да  |Да  |   |   |
|Windows 8                           |   |Да  |Да  |Да  |Да  |   |   |
|Windows 7 с пакетом обновления 1 (SP1)                       |   |   |Да  |Да  |Да  |Да  |   |
|Windows Vista с пакетом обновления 2 (SP2)                   |   |   |Да  |Да  |Да  |Да  |Да  |
|Windows XP с пакетом обновления 3 (SP3)                      |   |   |   |   |   |   |Да  |

 Следующих Linux и Mac, версии операционной системы (только 64-разрядная) поддерживаются с версии драйвера Microsoft PHP:

|PHP для SQL Server версии драйвера&#8594;<br />&#8595; операционная система|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|--|---|---|---|---|---|---|---|---|
|Ubuntu 18.04 (64-разрядная версия)               |Да  |   |   |   |   |   |   |   |
|Ubuntu 17.10 (64-разрядная версия)               |Да  |Да  |   |   |   |   |   |   |
|Ubuntu 16.04 (64-разрядная версия)               |Да  |Да  |Да  |Да  |   |   |   |   |
|Ubuntu 15.10 (64-разрядная версия)               |   |   |Да  |   |   |   |   |   |
|Ubuntu 15.04 (64-разрядная версия)               |   |   |   |Да  |   |   |   |   |
|Debian 9 (64-разрядная версия)                   |Да  |Да  |   |   |   |   |   |   |
|Debian 8 (64-разрядная версия)                   |Да  |Да  |Да  |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64-разрядная версия) |Да  |Да  |Да  |Да  |   |   |   |   |
|SuSE Enterprise Linux 12 (64-разрядная версия)   |Да  |Да  |   |   |   |   |   |   |
|macOS High Sierra (64-разрядная версия)          |Да  |   |   |   |   |   |   |   |
|macOS Sierra (64-разрядная версия)               |Да  |Да  |Да  |   |   |   |   |   |
|macOS El Capitan (64-разрядная версия)           |Да  |Да  |Да  |   |   |   |   |   |

## <a name="see-also"></a>См. также:  
[Заметки о выпуске](../../connect/php/release-notes-for-the-php-sql-driver.md)

[Ресурсы поддержки](../../connect/php/support-resources-for-the-php-sql-driver.md)

[Требования к системе](../../connect/php/system-requirements-for-the-php-sql-driver.md)

---
title: "Новые возможности Analytics Platform System — хранилища данных с горизонтальным масштабированием"
author: happynicolle
ms.author: nicw;barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "В разделе новые возможности Microsoft® Analytics Platform System масштабирования на локальном устройстве, на котором размещена MPP SQL Server Parallel Data Warehouse."
ms.date: 11/28/2016
ms.topic: article
ms.openlocfilehash: eeeb41045527e72856edfb8bdb40becc462bde07
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="whats-new-in-analytics-platform-system-2016-a-scale-out-mpp-data-warehouse"></a>Новые возможности 2016 системы платформы аналитики, масштабируемого хранилища данных MPP
В разделе новые возможности в Microsoft® Analytics Platform System (APS) 2016 последнее обновление устройства для масштабирования на локальном устройстве, на котором размещена MPP SQL Server Parallel Data Warehouse. 

## <a name="sql-server-2016"></a>SQL Server 2016

APS 2016 запускается на последний выпуск SQL Server 2016 и использует по умолчанию уровень совместимости 130.  SQL Server 2016 позволяет поддерживать некоторые новые функции, такие как вторичные индексы для кластеризованных индексов columnstore и Kerberos для PolyBase. 


## <a name="t-sql"></a>T-SQL
APS 2016 поддерживает эти улучшения совместимости T-SQL.  Эти дополнительные языковые элементы упрощают процесс миграции с SQL Server и другим источникам данных. 

- [Параметры сортировки уровня столбцов SQL][] теперь поддерживаются в дополнение к параметры сортировки Windows.
- [Некластеризованные индексы в кластеризованных индексах columnstore][] повысить производительность запросов, которые выполняют поиск конкретного значения в кластеризованном индексе. 
- [ВЫБЕРИТЕ... В][] 
- [sp_spaceused()][] отображает место на диске используется или зарезервировано в таблицу или базу данных.
- [Широкие таблицы][] поддержки является таким же, как SQL Server 2016. Предыдущие ограничение 32K для размера строки больше не существует. 

### <a name="data-types"></a>Типы данных

- [VARCHAR(max)][], [NVARCHAR(MAX)][] и [VARBINARY(MAX)][]. Эти типы данных больших ОБЪЕКТОВ имеют максимальный размер, равный 2 ГБ. Для загрузки этих объектов используйте [программа bcp][]. Polybase и dwloader в настоящее время не поддерживают эти типы данных. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [ЧИСЛОВЫЕ][] и типов данных DECIMAL.

### <a name="window-functions"></a>Оконные функции

- [ROWS или RANGE][] в предложении OVER инструкции SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

### <a name="security-functions"></a>Функции безопасности

- [CHECKSUM()][] и [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

### <a name="additional-functions"></a>Дополнительные функции

- [ФУНКЦИИ NEWID()][]
- [RAND()][]

## <a name="polybasehadoop-enhancements"></a>Усовершенствования PolyBase/Hadoop

- Совместимость с Hortonworks HDP 2.4 и HDP 2.5
- Поддержка проверки подлинности Kerberos через учетные данные уровня базы данных
- Поддержка учетных данных с большими двоичными объектами хранилища Azure

## <a name="install-and-upgrade-enhancements"></a>Установка и обновление усовершенствования

### <a name="enterprise-architecture-updates"></a>Архитектура обновления предприятия
Обновление существующего устройства до APS 2016 устанавливает последнюю версию встроенного по и обновления драйверов, включая исправления безопасности. 

Новым устройством из HPE или DELL содержит все последние обновления, а также:

- Создание процессоров, поддерживаемых (Broadwell)
- Обновление до DDR4 модули памяти DIMM
- Повышенная пропускная способность модуля памяти DIMM

### <a name="integration"></a>Интеграция

- Полное доменное имя (FQDN) поддержка делает можно установить доверие домена к устройству. 
- Чтобы использовать полное доменное имя, необходимо выполнить полное обновление и участия в программе во время обновления. 

### <a name="reduced-downtime"></a>Сокращение времени простоя
Установка или обновление до APS 2016 работает быстрее и требует меньше времени простоя, чем предыдущие выпуски. Чтобы уменьшить время простоя, установки или обновления. 

 - И упрощает применение обновлений WSUS с помощью образа, содержащего все обновления через июня 2016 г.
 - Область применения обновлений безопасности с обновлениями драйверов и встроенного по
 - Размещает последние исправления и служебную программу проверки устройством (PAV) на устройстве, так, чтобы они готовы к установке с нет необходимости загружать их.


<!--MSDN references-->
[database compatibility level 130]:https://msdn.microsoft.com/library/bb510680.aspx
[Параметры сортировки уровня столбцов SQL]:https://msdn.microsoft.com/library/ms143726.aspx
[Некластеризованные индексы в кластеризованных индексах columnstore]:https://msdn.microsoft.com/library/ms188783.aspx
[VARCHAR(max)]:https://msdn.microsoft.com/library/ms176089.aspx
[NVARCHAR(MAX)]:https://msdn.microsoft.com/library/ms186939.aspx
[VARBINARY(MAX)]:https://msdn.microsoft.com/library/ms188362.aspx
[SYSNAME]:https://msdn.microsoft.com/library/ms188021.aspx
[ВЫБЕРИТЕ... В]:https://msdn.microsoft.com/library/ms188029.aspx
[sp_spaceused()]:https://msdn.microsoft.com/library/ms188776.aspx
[Широкие таблицы]:https://msdn.microsoft.com/library/ms143432.aspx
[BULK INSERT]:https://msdn.microsoft.com/library/ms188365.aspx
[программа bcp]:https://msdn.microsoft.com/library/ms162802.aspx
[UNIQUEIDENTIFIER]:https://msdn.microsoft.com/library/ms187942.aspx
[ЧИСЛОВЫЕ]:https://msdn.microsoft.com/library/ms187746.aspx
[ROWS или RANGE]:https://msdn.microsoft.com/library/ms189461.aspx
[FIRST_VALUE]:https://msdn.microsoft.com/library/hh213018.aspx
[LAST_VALUE]:https://msdn.microsoft.com/library/hh231517.aspx
[CUME_DIST]:https://msdn.microsoft.com//library/hh231078.aspx
[PERCENT_RANK]:https://msdn.microsoft.com/library/hh213573.aspx
[CHECKSUM()]:https://msdn.microsoft.com/library/ms189788.aspx
[BINARY_CHECKSUM()]:https://msdn.microsoft.com/library/ms173784.aspx
[HAS_PERMS_BY_NAME()]:https://msdn.microsoft.com/library/ms189802.aspx
[ФУНКЦИИ NEWID()]:https://msdn.microsoft.com/library/ms190348.aspx
[RAND()]:https://msdn.microsoft.com/library/ms177610.aspx


  

  



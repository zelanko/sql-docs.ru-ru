---
title: Обновлено - подключиться к SQL Server docs | Документы Microsoft
description: Отображение фрагментов обновленное содержимое для последних измененных в документации, для подключения к Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: connect
ms.date: 02/03/2018
ms.openlocfilehash: da7ff58d5930acb084220c8d0364147ae93ed963
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>Новые и недавно обновленные: подключение к SQL Server



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон дат обновлений:* &nbsp; **03.12.2017**&nbsp;–&nbsp;**03.02.2018**
- *Предметной области:* &nbsp; **подключение к SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


***Сейчас новые статьи отсутствуют.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Использование постоянного шифрования с драйвером ODBC для SQL Server](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-using-always-encrypted-with-the-odbc-driver-for-sql-serverodbcusing-always-encrypted-with-the-odbc-drivermd"></a>1. &nbsp; [Использование постоянного шифрования с драйвером ODBC для SQL Server](odbc/using-always-encrypted-with-the-odbc-driver.md)

*Обновлено: 2018-01-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 524.  ms.author= "v-chojas".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a52abae2a8f27c3b5bc411ef758610116a608f9f 352368eb269b98ab5ca3a9791fae2e70bf26277a  (PR=4686  ,  Filename=using-always-encrypted-with-the-odbc-driver.md  ,  Dirpath=docs\connect\odbc\  ,  MergeCommitSha40=82c9868b5bf95e5b0c68137ba434ddd37fc61072) -->



**Получить данные в частях с SQLGetData**

Перед шифрованием 17 драйвер ODBC для SQL Server, символьных и двоичных столбцов не удается получить в частях с SQLGetData. Можно сделать только один вызов SQLGetData, с буфером достаточной длины для хранения данных всего столбца.

**Отправлять данные в частях с SQLPutData**

Невозможно отправить данные для вставки или сравнения в частях с SQLPutData. Только один вызов SQLPutData можно сделать с помощью буфер, содержащий все данные. Для вставки данных long в зашифрованных столбцах, используйте массового копирования API-Интерфейсе, описанные в следующем разделе, с помощью входных данных файла.

**Зашифрованные money и smallmoney**

Шифрование **money** или **smallmoney** столбцов нельзя указать с помощью параметров, так как нет конкретного не этих типов, что приводит к ошибкам пересекаться тип операнда какие сопоставляется с типом данных ODBC.

**Массовое копирование зашифрованных столбцов**


Использование [функции массового копирования SQL](odbc/../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md) и **bcp** поддерживается применение служебной программы с постоянным шифрованием с момента 17 драйвер ODBC для SQL Server. Обычный текст (зашифрованный для вставки и расшифрованные на получение) и зашифрованного текста (передаются открытым текстом) может быть вставлен, а с помощью массового копирования (bcp_ *) API-интерфейсов и **bcp** программы.

- Для получения зашифрованных данных в виде varbinary(max) (например, для массовой загрузки в другой базе данных), подключение без `ColumnEncryption` параметр (или присвойте ей значение `Disabled`) и выполнения операции BCP OUT.

- Для вставки и извлечения открытого текста и позволить драйвер прозрачно выполнения шифрования и расшифровки как обязательный, параметр `ColumnEncryption` для `Enabled` достаточно. Функциональные возможности BCP API остается неизменным.

- Чтобы вставить зашифрованных данных в виде varbinary(max) (например, в полученных выше), установите `BCPMODIFYENCRYPTED` в значение TRUE и выполнять операции BCP IN. Чтобы быть расшифровываемой результирующих данных убедитесь, что целевой CEK столбца совпадает с параметром, из которого первоначально был получен зашифрованный текст.







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи


- [Новые + обновленные (1+3):&nbsp; **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (0+1):&nbsp; **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+1):&nbsp; **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1):&nbsp; **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (12+1): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (6+2):&nbsp; **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (15+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (2+9):&nbsp; **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (1+0):&nbsp; **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+1):&nbsp; **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(1+1):&nbsp; **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1):&nbsp; **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+2):&nbsp; **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2):&nbsp; **Transact-SQL**](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи


- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новый + обновленные (0 + 0): **объектов данных ActiveX (ADO) для SQL** документы](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../samples/new-updated-samples.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)



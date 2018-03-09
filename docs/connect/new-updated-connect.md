---
title: "Обновлено - подключиться к SQL Server docs | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации, для подключения к Microsoft SQL Server."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: connect
ms.date: 02/03/2018
ms.openlocfilehash: cc4eb05dc4dcd74623c8ce7dfa7b7842449d79b6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>Новые и недавно обновленные: подключение к SQL Server



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2017 г-12-03** &nbsp; - в - &nbsp; **2018-02-03**
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

### <a name="1-nbsp-using-always-encrypted-with-the-odbc-driver-for-sql-serverodbcusing-always-encrypted-with-the-odbc-drivermd"></a>1. &nbsp;[Использование постоянного шифрования с драйвером ODBC для SQL Server](odbc/using-always-encrypted-with-the-odbc-driver.md)

*Обновлено: 2018-01-22* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

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







## <a name="similar-articles-about-new-or-updated-articles"></a>Аналогичные статьи о новых или обновленных статьях

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметной области, *сделать* новыми или были недавно обновлены статьи


- [Новый + обновленные (1 + 3):&nbsp; **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (0 + 1):&nbsp; **Analytics Platform System для SQL** документы](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новый + обновленные (0 + 1):&nbsp; **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (0 + 1):&nbsp; **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (12 + 1): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (6 + 2):&nbsp; **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (15 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новый + обновленные (2 + 9):&nbsp; **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (1 + 0):&nbsp; **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (1 + 1):&nbsp; **операций SQL Studio** документы](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новый + обновленные (1 + 1):&nbsp; **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (0 + 1):&nbsp; **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (1 + 2):&nbsp; **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 2):&nbsp; **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметной области, которые выполняют *не* иметь любой новыми или были недавно обновлены статьи


- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новый + обновленные (0 + 0): **объектов данных ActiveX (ADO) для SQL** документы](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../sample/new-updated-sample.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)



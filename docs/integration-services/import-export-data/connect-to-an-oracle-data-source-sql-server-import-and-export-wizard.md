---
title: Подключение к источнику данных Oracle (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/29/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b0bd1f5a-34dd-4be3-9ac8-f9f87727781b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 202527022ccc78a4f0c89bb3cfbfe775ecde207b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914141"
---
# <a name="connect-to-an-oracle-data-source-sql-server-import-and-export-wizard"></a>Подключение к источнику данных Oracle (мастер импорта и экспорта SQL Server)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


В этом разделе показано, как подключаться к источникам данных **Oracle** со страницы **Выбор источника данных** или **Выбор назначения** в мастере импорта и экспорта SQL Server. Для подключения к Oracle можно использовать ряд поставщиков данных.

> [!IMPORTANT]
> Подробные требования и необходимые условия для подключения к базе данных Oracle выходят за рамки этой статьи Майкрософт. В ней предполагается, что у вас уже установлено клиентское программное обеспечение Oracle и вы можете успешно подключиться к целевой базе данных Oracle. Для получения дополнительных сведений обратитесь к администратору базы данных Oracle или к документации по Oracle.

## <a name="connect-to-oracle-with-the-net-framework-data-provider-for-oracle"></a>Подключение к Oracle с помощью поставщика данных платформы .NET Framework для Oracle
После выбора элемента **Поставщик данных .NET Framework для Oracle** на странице **Выбор источника данных** или **Выбор назначения** мастера появится сгруппированный список параметров для поставщика. Многие из них могут быть вам незнакомы или иметь непонятные имена. Однако вам достаточно указать всего два или три параметра. Остальные параметры можно пропустить.

> [!NOTE]
> Параметры подключения для этого поставщика данных одинаковы независимо от того, является ли Oracle источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

|Необходимые сведения|Поставщик данных .NET Framework для свойства Oracle|
|---|---|
|Имя сервера|**Источник данных**|
|Сведения для проверки подлинности (имя входа)|**Идентификатор пользователя** и **Пароль**; или **Встроенная система безопасности**|
|||

Вам не нужно вводить строку подключения в поле **ConnectionString** списка. После ввода отдельных значений для имени сервера Oracle (**источника данных**) и информации для входа мастер собирает строку подключения из отдельных свойств и их значений. 

![Подключение к Oracle с помощью поставщика .NET](../../integration-services/import-export-data/media/connect-to-oracle-with-net-provider.jpg)

## <a name="connect-to-oracle-with-the-microsoft-odbc-driver-for-oracle"></a>Подключение к Oracle с помощью драйвера Microsoft ODBC для Oracle
Драйверы ODBC не приводятся в раскрывающемся списке источников данных. Чтобы подключиться с помощью драйвера ODBC, сначала выберите **поставщик данных .NET Framework для ODBC** в качестве источника данных на странице **Выбор источника данных** или **Выбор назначения**. Этот поставщик служит оболочкой для драйвера ODBC.

Ниже показан экран, который появляется сразу после выбора поставщика данных .NET Framework для ODBC.

![Подключение к Oracle с помощью ODBC ранее](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-oracle"></a>Указываемые параметры (драйвер ODBC для Oracle)

> [!NOTE]
> Параметры подключения для этого поставщика данных и драйвера ODBC одинаковы независимо от того, является ли сервер Oracle источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

Чтобы подключиться к Oracle с помощью драйвера ODBC для Oracle, соберите строку подключения, используя указанные ниже параметры и их значения. Полный формат строки подключения приведен после списка параметров.

> [!TIP]
> Вы можете получить помощь в построении строки подключения. Кроме того, вместо указания строки подключения вы можете предоставить существующее имя DSN (имя источника данных) или создать новое. Дополнительные сведения об этих возможностях см. в разделе [Подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Драйвер**  
Имя драйвера ODBC — **Microsoft ODBC for Oracle**.

**Server**  
Имя сервера Oracle. 

**Uid** и **Pwd**   
Идентификатор пользователя и пароль для подключения.

### <a name="connection-string-format"></a>Формат строки подключения
Ниже приведен формат типичной строки подключения.

```console
Driver={Microsoft ODBC for Oracle};Server=myServerAddress;Uid=myUsername;Pwd=myPassword;
```

### <a name="enter-the-connection-string"></a>Ввод строки подключения
Введите строку подключения в поле **ConnectionString** либо введите имя DSN в поле **Dsn** на странице **Выбор источника данных** или **Выбор назначения**. После того как вы введете строку подключения, мастер проанализирует ее и отобразит отдельные свойства и их значения в списке.

Ниже показан экран, который появляется после ввода строки подключения.

![Подключение к Oracle с помощью ODBC](../../integration-services/import-export-data/media/connect-to-oracle-with-odbc.jpg)

## <a name="whats-my-oracle-server-name"></a>Какое имя у моего сервера Oracle?
Выполните один из следующих запросов, чтобы узнать имя сервера Oracle.

`SELECT host_name FROM v$instance`

или диспетчер конфигурации служб

`SELECT sys_context('USERENV','SERVER_HOST') FROM dual`

## <a name="other-data-providers-and-more-info"></a>Другие поставщики данных и дополнительные сведения
Сведения о подключении к Oracle с помощью поставщика данных, не представленного в этом списке, см. в разделе [Строки подключения Oracle](https://www.connectionstrings.com/oracle/). Этот сторонний сайт также содержит дополнительные сведения о поставщиках данных и параметрах подключения, описанных на этой странице.

## <a name="see-also"></a>См. также раздел
[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


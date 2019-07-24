---
title: Список исправленных ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 096c11c018294cbc92b2be13801d6cd953548fff
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264013"
---
# <a name="list-of-bugs-fixed"></a>Список исправленных ошибок

На этой странице содержится список ошибок, исправленных в каждом выпуске [!INCLUDE[msCoName](../../includes/msconame_md.md)] , начиная с ODBC Driver 17 для[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] драйвере ODBC 17,3 для[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Исправлено утечку памяти для дескриптора события отправки TCP
- Исправлена проблема переопределения enum _SQL_FILESTREAM_DESIRED_ACCESS в файле заголовка msodbcsql. h
- Исправлена отсутствующая ACCESS_TOKEN и связанное с ПРОВЕРКой подлинности определение в файле заголовка msodbcsql. h для Linux

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] драйвере ODBC 17,2 для[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Исправлено сообщение об ошибке Azure Active Directory проверки подлинности
- Исправлено обнаружение кодирования, если переменные среды языкового стандарта заданы по-разному
- Исправлена аварийное завершение при отключении с восстановлением соединения
- Устранено обнаружение актуальности подключения
- Исправлено неправильное обнаружение закрытых сокетов.
- Устранено бесконечное ожидание при попытке освободить маркер инструкции во время восстановления после сбоя
- Исправлено неправильное поведение при удалении, если в Windows установлены обе версии 13 и 17
- Фиксированное поведение расшифровки на более старой платформе Windows (Windows 7, 8 и 2012)
- Исправлена проблема с кэшем при использовании проверки подлинности ADAL в Windows
- Исправлена проблема блокировки и перезаписи журналов трассировки в Windows.

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] драйвере ODBC 17,1 для[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Исправлена задержка 1 секунда при вызове SQLFreeHandle с включенным режимом MARS и атрибутом подключения "Encrypt = Yes"
- Исправлена ошибка 22003 при сбое в SQLGetData, если размер переданного буфера меньше, а затем получаемые данные (Windows)
- Исправлены усеченные сообщения об ошибках ADAL
- Исправлена редкие ошибки в 32-разрядной системе Windows при преобразовании числа с плавающей запятой в целое число
- Исправлена проблема, при которой при вставке двойного в десятичное поле с помощью Always Encrypted возвращается ошибка усечения данных.
- Исправлено предупреждение в установщике MacOS
- Исправлена ошибка отправки неверного состояния в SQL Server во время попытки восстановления сеанса, когда включены отказоустойчивость подключения и пул соединений, что приводит к удалению сеанса сервером.

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 для[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Исправлена ошибка, при которой при использовании проверки подлинности Kerberos может произойти сбой при выполнении инструкции INSERT с ошибкой "отказано в доступе"
- Удален обходной путь для ошибки unixODBC, представленной в версии "2.3.1" (драйвер вдвое превышает размеры некоторых буферов, переданных в unixODBC).
- Исправлена устойчивость подключения (повторное подключение) при использовании ColumnEncryption = Enabled
- Исправлена ошибка создания имени DSN, где при использовании параметра "Active Directoryная Интерактивная проверка подлинности" окно проверки подлинности Azure может перестать отвечать (Windows)
- Устранено редкий сбой при завершении работы ODBC при включении асинхронного выполнения (происходит при очистке маркера подключения).
- Исправлена проблема, из – за которой драйвер SQL выдавал высокий уровень потребления ресурсов ЦП при выполнении длинных хранимых процедур.
- Исправлена невозможность получения данных в зашифрованном столбце varbinary (max) без преобразования
- Исправлена проблема, из-за которой зашифрованный столбец типа varchar (max) со значением NULL выберется с помощью SQLGetData () для статического курсора, а следующий столбец также имеет значение null, даже если он содержит данные.
- Исправлена проблема с получением поля varbinary (max) с Always Encrypted on.
- Исправлена ошибка setlocale (), не работающая с Always Encrypted
- Исправлена проблема с возвратом ошибки SQLDescribeParam () при вызове для параметра хранимой процедуры типа XML с Always Encrypted on.
- Исправленные знаки подчеркивания не работают в SQLTables
- Исправлена ошибка, при которой данные иврита (varchar) усекаются при возврате расширенных символов в Linux.
- Исправлена проблема с запросом Shift-JIS в кодировке char/varchar из приложения UTF-8.
- Исправлена ошибка, при которой вызов SQLGetInfo с параметром SQL_DRIVER_NAME вернул имя файла в формате Linux в MacOS
- Исправлена проблема, при которой загрузка символьных данных Windows-1252 с использованием входных файлов размером более 32 КБ в столбцы типа VARCHAR с помощью служебной программы BCP приведет к сбоям.

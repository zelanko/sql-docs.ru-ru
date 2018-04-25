---
title: Список ошибок, исправленных | Документы Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
caps.latest.revision: 69
author: v-makouz
ms.author: genemi
manager: kenvh
ms.workload: Active
ms.openlocfilehash: 58da69ed6c4b7b046f8d1bc1ddf4e23b71b99a29
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="list-of-bugs-fixed"></a>Список ошибок, исправленных

Эта страница содержит список ошибок, исправленных в каждом из выпусков, начиная с [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17 драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17,1 драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

- Исправлена 1-секундная задержка при вызове SQLFreeHandle с включенным режимом MARS и атрибут соединения «Encrypt = yes»
- Исправлена ошибка 22003 сбой в SQLGetData, если размер буфера, переданного в меньше второго, а затем извлекаемых данных (Windows)
- Исправлена усеченное ADAL ошибок
- Исправлена ошибка редких на 32-разрядной версии Windows, при преобразовании значение с плавающей запятой в целое число
- Устранена проблема, где Вставка double в десятичное поле с постоянным шифрованием на вернет ошибку усечение данных
- Исправлено в установщик MacOS предупреждение
- Фиксированный отправку неверном состоянии для SQL Server при попытке восстановления сеанса, если устойчивость подключений и организации пулов соединений оба включены, вызывая сеанса для удаления с сервера

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17 драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

- Исправлена ошибка, если при использовании проверки подлинности Kerberos, инструкции bulk insert может завершиться с ошибкой «доступ запрещен»
- Удален обходной путь представлен в версии ниже 2.3.1 unixODBC ошибки (драйвер двойной размеры некоторые буферы, передаваемый unixODBC)
- Исправлена устойчивость подключений (повторное подключение) висячей при использовании ColumnEncryption = включено
- Исправлена ошибка создания источника данных, где при с помощью «Проверка подлинности Active Directory для интерактивного» параметра проверки подлинности Azure окна может стать не отвечает (Windows)
- Исправлена редких сбой во время завершения работы ODBC при включении асинхронного выполнения (произошло при удалении дескриптора соединения)
- Устранена проблема, при котором драйвер SQL вызвал высокую нагрузку на ЦП при выполнении долго хранимых процедур
- Фиксированный невозможность получения данных в столбец varbinary(max) зашифрованные без преобразования
- Устранена проблема, когда после null varchar(max) зашифрованного столбца получается с помощью функции SQLGetData() для статического курсора, следующий столбец будет также обнулением даже при наличии данных
- Устранена проблема с выборкой varbinary(max) поле с постоянным шифрованием на
- Устранена проблема setlocale() не работает с постоянным шифрованием
- Исправлена проблема с SQLDescribeParam(), возвращая ошибку при вызове на параметр процедуры типа XML, хранящегося с постоянным шифрованием
- Фиксированный escape-символы подчеркивания, не работает в SQLTables
- Исправлена ошибка, где данные иврита (varchar) будут усечены при возврате в виде расширенных символов в Linux
- Устранена проблема с запросами в кодировке Shift-JIS char и varchar из приложения UTF-8
- Исправлять ошибку, в которых вызов SQLGetInfo с параметром SQL_DRIVER_NAME возвращает filename стиле Linux на MacOS
- Устранена проблема, где файлы размером более 32 КБ, байтов в столбцы типа VARCHAR, с помощью программы bcp приведет к возникновению сбоев при загрузке Windows-1252 символьных данных, используя входные данные

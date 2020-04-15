---
title: Автоперевод данных о персонажах (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a8672f748af8d643fa39038be030efa5d434dc8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297886"
---
# <a name="autotranslation-of-character-data"></a>Автоматическое преобразование символьных данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Данные о персонажах, такие как переменные символов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI, заявленные с SQL_C_CHAR или данные, хранящиеся в использовании **символа,** **varchar**или типах **текстовых** данных, могут представлять только ограниченное число символов. Символьные данные, в которых для обозначения одного символа требуется один байт данных, могут представлять только 256 символов. Для интерпретации значений, содержащихся в переменных SQL_C_CHAR, используются кодовые страницы ANSI (ACP) клиентского компьютера. Значения, хранящиеся с помощью **char,** **varchar**или типы **текстовых** данных на сервере, оцениваются с помощью ACP сервера.  
  
 Если и сервер, и клиент имеют один и тот же ACP, то у них нет проблем в интерпретации значений, хранящихся в SQL_C_CHAR, **char,** **varchar**или **текстовых** объектах. Если сервер и клиент имеют различные ACPs, то SQL_C_CHAR данные от клиента могут быть интерпретированы как другой символ на сервере, если он используется в **символ,** **varchar**, или **текстовые** столбцы, переменные или параметры. Например, байт символа, содержащий значение 0xA5, интерпретируется как символ на компьютере с помощью кодовой страницы 437 и интерпретируется как знак иены (яп. ) на странице кода компьютера 1252.  
  
 Символы в формате Юникода записываются с использованием двух байт данных. В стандарт Юникод включены все дополнительные символы, поэтому все символы Юникода интерпретируются всеми компьютерами одинаково.  
  
 Функция AutoTranslate драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC пытается свести к минимуму проблемы при перемещении данных символов между клиентом и сервером с различными страницами кода. AutoTranslate может быть установлен в строке подключения [S'LDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), в строке конфигурации [S'LConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md), или при настройке источников данных для драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC с помощью администратора ODBC.  
  
 Когда AutoTranslate настроен на "нет", преобразования не выполняются на данных, перемещаемых между SQL_C_CHAR переменными на клиенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и **символе,** **varchar,** или **текстовых** столбцах, переменных или параметрах в базе данных. Эти битовые шаблоны могут по-разному интерпретироваться клиентом и сервером, если данные содержат символы национального алфавита, и два компьютера имеют различные кодовые страницы. Данные интерпретируются единообразно, если оба компьютера используют одну и ту же кодовую страницу.  
  
 Когда AutoTranslate настроен на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "да", драйвер Native Client ODBC использует Unicode для преобразования данных, перемещаемых между SQL_C_CHAR переменными на клиенте и **символе,** **varchar**, или **текстовых** столбцах, переменных или параметрах в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных:  
  
-   Когда данные отправляются из SQL_C_CHAR переменной клиента в **символ,** **varchar**, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **текстовый** столбец, переменная или параметр в базе данных, драйвер ODBC сначала преобразуется из SQL_C_CHAR в Unicode с помощью ACP клиента, а затем от Unicode обратно к символу с помощью ACP сервера.  
  
-   Когда данные отправляются с **символа,** **varchar**, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **текстовый** столбец, переменная, или параметр в базе данных в SQL_C_CHAR переменной на клиента, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] родной клиент ODBC драйвер сначала преобразует из символа в Unicode с помощью ACP сервера, а затем из Unicode обратно в SQL_C_CHAR с помощью ACP клиента.  
  
 Поскольку все эти преобразования выполняются драйвером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC, исполняющим на клиенте, сервер ACP должен быть одной из страниц кода, установленных на клиентском компьютере.  
  
 Выполнение символьных преобразований с использованием формата Юникод гарантирует правильное преобразование всех символов, существующих на обеих кодовых страницах. Но если символ имеется на одной кодовой странице и отсутствует на другой, этот символ не может быть представлен на целевой кодовой странице. Например, в кодовой странице 1252 имеется символ зарегистрированного товарного знака (®), а на кодовой странице 437 такого символа нет.  
  
 Настройка AutoTranslate не оказывает влияния на эти преобразования.  
  
-   Перемещение данных между переменными SQL_C_CHAR клиента и Unicode **nchar,** **nvarchar**или **ntext** столбцов, переменных или параметров в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базах данных.  
  
-   Перемещение данных между переменными Unicode SQL_C_WCHAR клиентом и **символом,** **varchar**или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **текстовыми** столбиками, переменными или параметрами в базах данных.  
  
 Данные всегда нужно преобразовывать при переходе из символьного формата в Юникод.  
  
## <a name="see-also"></a>См. также:  
 [Результаты обработки &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  

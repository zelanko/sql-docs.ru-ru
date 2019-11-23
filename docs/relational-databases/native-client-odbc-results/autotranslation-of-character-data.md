---
title: Автоматическое преобразование символьных данных | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c08a0987e11f25c3f5b535d8d26526db5bb14a38
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73779177"
---
# <a name="autotranslation-of-character-data"></a>Автоматическое преобразование символьных данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Символьные данные, такие как переменные символов ANSI, объявленные с SQL_C_CHAR или данными, хранящимися в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием типов данных **char**, **varchar**или **Text** , могут представлять только ограниченное число символов. Символьные данные, в которых для обозначения одного символа требуется один байт данных, могут представлять только 256 символов. Для интерпретации значений, содержащихся в переменных SQL_C_CHAR, используются кодовые страницы ANSI (ACP) клиентского компьютера. Значения, хранимые с помощью типов данных **char**, **varchar**или **Text** на сервере, оцениваются с помощью ACP сервера.  
  
 Если сервер и клиент имеют один и тот же ACP, у них нет проблем с интерпретацией значений, хранящихся в SQL_C_CHAR, **char**, **varchar**или **Text** Objects. Если сервер и клиент имеют разные ACP, то SQL_C_CHAR данные с клиента могут интерпретироваться как разные символы на сервере, если они используются в столбцах **char**, **varchar**или **Text** , переменных или параметрах. Например, байт символов, содержащий значение 0xA5, интерпретируется как символ «счет» на компьютере с кодовой страницей 437 и интерпретируется как знак «¥» на компьютере с кодовой страницей 1252.  
  
 Символы в формате Юникода записываются с использованием двух байт данных. В стандарт Юникод включены все дополнительные символы, поэтому все символы Юникода интерпретируются всеми компьютерами одинаково.  
  
 Функция автоматического преобразования драйвера ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается устранить проблемы при переносе символьных данных между клиентом и сервером с разными кодовыми страницами. Параметр автотрансляции можно задать в строке подключения [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), в строке конфигурации [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)или при настройке источников данных для драйвера ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для собственного клиента с помощью администратора ODBC.  
  
 Если параметру автоперевода присвоено значение "нет", преобразования данных, перемещаемых между переменными SQL_C_CHAR на клиенте и в столбцах **типа char**, **varchar**или **text** , в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не выполняются. Эти битовые шаблоны могут по-разному интерпретироваться клиентом и сервером, если данные содержат символы национального алфавита, и два компьютера имеют различные кодовые страницы. Данные интерпретируются единообразно, если оба компьютера используют одну и ту же кодовую страницу.  
  
 Если для параметра автоперевода задано значение "Да", то драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует Юникод для преобразования данных, перемещаемых между переменными SQL_C_CHAR на клиенте, а также столбцами **типа char**, **varchar**или **Text** , переменными или параметрами в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Когда данные отправляются из переменной SQL_C_CHAR на клиенте в столбец **типа char**, **varchar**или **Text** , переменную или параметр в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных, драйвер ODBC сначала преобразует из SQL_C_CHAR в Юникод с помощью ACP клиента, а затем обратно в кодировке Юникод, используя ACP сервера.  
  
-   Когда данные отправляются из столбца **типа char**, **varchar**или **Text** , переменной или параметра в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных в SQL_C_CHARую переменную на клиенте, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента сначала ПРЕОБРАЗУЕТ символы в Юникод с помощью ACP сервера, а затем обратно из Юникода в SQL_C_CHAR с помощью ACP клиента.  
  
 Поскольку все эти преобразования выполняются с помощью драйвера ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который выполняется на клиенте, в качестве сервера может использоваться одна из кодовых страниц, установленных на клиентском компьютере.  
  
 Выполнение символьных преобразований с использованием формата Юникод гарантирует правильное преобразование всех символов, существующих на обеих кодовых страницах. Но если символ имеется на одной кодовой странице и отсутствует на другой, этот символ не может быть представлен на целевой кодовой странице. Например, в кодовой странице 1252 имеется символ зарегистрированного товарного знака (®), а на кодовой странице 437 такого символа нет.  
  
 Настройка AutoTranslate не оказывает влияния на эти преобразования.  
  
-   Перемещение данных между символьными SQL_C_CHAR клиентскими переменными и столбцами, переменными или **параметрами Юникода в Юникоде,** **nvarchar**или **ntext** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базах данных.  
  
-   Перемещение данных между клиентскими переменными SQL_C_WCHAR Юникода и символьными столбцами **char**, **varchar**или **Text** , переменными или параметрами в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базах данных.  
  
 Данные всегда нужно преобразовывать при переходе из символьного формата в Юникод.  
  
## <a name="see-also"></a>См. также статью  
 [Обработка результатов &#40;в&#41; ODBC](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  

---
title: Автоматическое преобразование символьных данных | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cca068f3e9ed8120449f83105998e2355704ae40
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35700045"
---
# <a name="autotranslation-of-character-data"></a>Автоматическое преобразование символьных данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Символьные данные, такие как ANSI символьные переменные, объявленные с помощью SQL_C_CHAR или данные, хранящиеся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью **char**, **varchar**, или **текст** типов данных можно представляют только ограниченное число знаков. Символьные данные, в которых для обозначения одного символа требуется один байт данных, могут представлять только 256 символов. Для интерпретации значений, содержащихся в переменных SQL_C_CHAR, используются кодовые страницы ANSI (ACP) клиентского компьютера. Значения, сохраненные с помощью **char**, **varchar**, или **текст** типов данных на сервере, вычисляются с помощью ACP сервера.  
  
 Если сервер и клиент имеют та же кодовая страница, то они имеют значения, хранящиеся в SQL_C_CHAR, без проблем **char**, **varchar**, или **текст** объектов. Если сервер и клиент имеют разные кодовые страницы ANSI, то данные SQL_C_CHAR от клиента может интерпретироваться как другой символ на сервере, если он используется в **char**, **varchar**, или **текста** столбцов, переменных или параметров. Например символьный байт, содержащий значение 0xA5, интерпретируется как символ Ñ на компьютере, использующем кодовую страницу 437 и интерпретируется как знак иены (¥) на компьютере под управлением кодовую страницу 1252.  
  
 Символы в формате Юникода записываются с использованием двух байт данных. В стандарт Юникод включены все дополнительные символы, поэтому все символы Юникода интерпретируются всеми компьютерами одинаково.  
  
 Функции AutoTranslate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента пытается свести к минимуму проблемы при перемещении символьных данных между клиентом и сервером, которые имеют различные кодовые страницы. Функция AutoTranslate может быть задано в строке соединения [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), в строке конфигурации [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md), или при настройке источников данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC для собственного клиента драйвер с помощью администратора ODBC.  
  
 Если AutoTranslate имеет значение «no», не подвергаются преобразованиям данные, перемещаемые между переменными SQL_C_CHAR на клиенте и **char**, **varchar**, или **текст** столбцов, переменных, или параметров в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Эти битовые шаблоны могут по-разному интерпретироваться клиентом и сервером, если данные содержат символы национального алфавита, и два компьютера имеют различные кодовые страницы. Данные интерпретируются единообразно, если оба компьютера используют одну и ту же кодовую страницу.  
  
 Если AutoTranslate задано значение «yes», [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента использует формат Юникод для преобразования данных, перемещаемых между переменными SQL_C_CHAR на клиенте и **char**, **varchar**, или **текст** столбцов, переменных или параметров в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных:  
  
-   Когда данные передаются из переменной SQL_C_CHAR на клиенте, чтобы **char**, **varchar**, или **текст** столбцу, переменной или параметра в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных ODBC драйвер сначала преобразует из SQL_C_CHAR в Юникод с использованием ACP клиента, затем из Юникода обратно в символ с помощью ACP сервера.  
  
-   При отправке данных из **char**, **varchar**, или **текст** столбцу, переменной или параметра в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных в переменную SQL_C_CHAR на клиенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер собственного клиента ODBC сначала преобразует символ Юникода с использованием ACP сервера, затем из Юникода обратно в SQL_C_CHAR, с использованием ACP клиента.  
  
 Поскольку все эти преобразования выполняются с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента, выполняемым на клиенте, ACP сервера должно быть одним из кодовых страниц, установленных на клиентском компьютере.  
  
 Выполнение символьных преобразований с использованием формата Юникод гарантирует правильное преобразование всех символов, существующих на обеих кодовых страницах. Но если символ имеется на одной кодовой странице и отсутствует на другой, этот символ не может быть представлен на целевой кодовой странице. Например, в кодовой странице 1252 имеется символ зарегистрированного товарного знака (®), а на кодовой странице 437 такого символа нет.  
  
 Настройка AutoTranslate не оказывает влияния на эти преобразования.  
  
-   Перемещение данных между символьными клиентскими переменными SQL_C_CHAR и Юникода **nchar**, **nvarchar**, или **ntext** столбцов, переменных или параметров в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
-   Перемещение данных между клиентскими переменными Юникод SQL_C_WCHAR и символ **char**, **varchar**, или **текст** столбцов, переменных или параметров в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
 Данные всегда нужно преобразовывать при переходе из символьного формата в Юникод.  
  
## <a name="see-also"></a>См. также  
 [Обработка результатов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  

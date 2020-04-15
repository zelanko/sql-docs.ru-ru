---
title: Эффекты опционов ИСО Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: adf37d03f5ea4f06be4d58e60deca68e10d45abb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297962"
---
# <a name="effects-of-iso-options"></a>Действие параметров ISO
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Стандарт ODBC близок к стандарту ISO, а приложения ODBC ожидают стандартного поведения от драйвера ODBC. Чтобы его поведение было более тесно соответствовать стандарту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC, водитель Native Client ODBC всегда использует любые параметры ISO, доступные в версии сервера S'L, с которым он подключается.  
  
 Когда [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] водитель Native Client ODBC подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]экземпляру, сервер обнаруживает, что клиент использует драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC, и устанавливает несколько вариантов.  
  
 Драйвер сам формирует эти инструкции; ODBC-приложение не посылает для этого никаких запросов. Установка этих параметров позволяет ODBC-приложениям, использующим драйвер, иметь лучшую переносимость, поскольку в этом случае поведение сервера более соответствует стандарту ISO.  
  
 Приложения на основе DB-Library обычно не вызывают включение этих параметров. Сайты, наблюдающий за различным поведением между клиентами ODBC или DB-Library [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при запуске одного и того же оператора S'L, не должны предполагать, что это указывает на проблему с драйвером Native Client ODBC. Сначала они должны повторно запустить заявление в среде DB-Library с теми же set опциями, которые будут использоваться драйвером [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC.  
  
 Поскольку пользователи и приложения могут в любое время включать и выключать параметры из набора SET, разработчики хранимых процедур и триггеров должны проводить тестирование своих процедур и триггеров как со включенными, так и с отключенными параметрами из этого набора. Это гарантирует, что триггеры и процедуры будут правильно работать независимо от того, какие параметры конкретное соединение установит при вызове триггера или процедуры. Если для работы триггера или хранимой процедуры требуется конкретное значение одного из этих параметров, инструкцию SET следует выполнить в начале триггера или хранимой процедуры. Она сохраняет силу только до завершения триггера или хранимой процедуры; после этого восстанавливается первоначальное значение параметра.  
  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливается также четвертый параметр SET, CONCAT_NULL_YIELDS_NULL. Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC не устанавливает эти параметры, если AnsiNPW-NO указан в источнике данных или на [s'LDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) или [S'LBrowseConnect.](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
 Как и варианты ISO, отмеченные ранее, драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC не включает QUOTED_IDENTIFIER опцию, если в источнике данных указана цитата ID-NO или на ни в **S'LDriverConnect,** ни на **S'LBrowseConnect.**  
  
 Чтобы драйвер мог узнавать текущие значения параметров SET, ODBC-приложения не должны задавать эти параметры с помощью инструкции языка [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET. Они могут задавать их только через параметры источника данных или соединения. Если приложение запускает инструкции SET, то инструкции SQL, создаваемые драйвером, могут быть неверными.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение заявлений &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [СЗЛДрайверКоннект](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  

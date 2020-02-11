---
title: Влияние параметров ISO | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebef85cf1deb2327122edfd536991f689b14c747
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206760"
---
# <a name="effects-of-iso-options"></a>Действие параметров ISO
  Стандарт ODBC близок к стандарту ISO, а приложения ODBC ожидают стандартного поведения от драйвера ODBC. Чтобы обеспечить более тесное соответствие поведения, определенного в стандарте ODBC, драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для собственного клиента всегда использует любые параметры ISO, доступные в версии SQL Server, с которой он подключается.  
  
 Когда драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для собственного клиента подключается к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], сервер обнаруживает, что клиент использует драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента и устанавливает несколько параметров в.  
  
 Драйвер сам формирует эти инструкции; ODBC-приложение не посылает для этого никаких запросов. Установка этих параметров позволяет ODBC-приложениям, использующим драйвер, иметь лучшую переносимость, поскольку в этом случае поведение сервера более соответствует стандарту ISO.  
  
 Приложения на основе DB-Library обычно не вызывают включение этих параметров. Сайты, отслеживающие различные поведения клиентов ODBC или DB-Library при выполнении одной и той же инструкции SQL, не предполагают, что это указывает на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проблему с драйвером ODBC для собственного клиента. Они должны сначала перезапустить инструкцию в среде DB-Library с теми же параметрами SET, которые использовались драйвером [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для собственного клиента.  
  
 Поскольку пользователи и приложения могут в любое время включать и выключать параметры из набора SET, разработчики хранимых процедур и триггеров должны проводить тестирование своих процедур и триггеров как со включенными, так и с отключенными параметрами из этого набора. Это гарантирует, что триггеры и процедуры будут правильно работать независимо от того, какие параметры конкретное соединение установит при вызове триггера или процедуры. Если для работы триггера или хранимой процедуры требуется конкретное значение одного из этих параметров, инструкцию SET следует выполнить в начале триггера или хранимой процедуры. Она сохраняет силу только до завершения триггера или хранимой процедуры; после этого восстанавливается первоначальное значение параметра.  
  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливается также четвертый параметр SET, CONCAT_NULL_YIELDS_NULL. Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для собственного клиента не устанавливает эти параметры в случае, если АНСИНПВ = No указано в источнике данных или в [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) или [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).  
  
 Как и параметры ISO, указанные ранее, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента не включает параметр QUOTED_IDENTIFIER on, если КУОТЕДИД = No указано в источнике данных или в **SQLDriverConnect** или **SQLBrowseConnect**.  
  
 Чтобы драйвер мог узнавать текущие значения параметров SET, ODBC-приложения не должны задавать эти параметры с помощью инструкции языка [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET. Они могут задавать их только через параметры источника данных или соединения. Если приложение запускает инструкции SET, то инструкции SQL, создаваемые драйвером, могут быть неверными.  
  
## <a name="see-also"></a>См. также:  
 [Исполнение инструкций &#40;ODBC&#41;](executing-statements-odbc.md)   
 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  

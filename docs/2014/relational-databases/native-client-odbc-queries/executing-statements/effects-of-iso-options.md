---
title: Действие параметров ISO | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206760"
---
# <a name="effects-of-iso-options"></a>Действие параметров ISO
  Стандарт ODBC близок к стандарту ISO, а приложения ODBC ожидают стандартного поведения от драйвера ODBC. Чтобы более точно соответствовать поведение, определенного в стандарте ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента всегда использует все параметры ISO, доступные в версии SQL Server, к которой он подключается.  
  
 Когда [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента подключается к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], сервер обнаруживает, что клиент использует [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента и устанавливает некоторые параметры.  
  
 Драйвер сам формирует эти инструкции; ODBC-приложение не посылает для этого никаких запросов. Установка этих параметров позволяет ODBC-приложениям, использующим драйвер, иметь лучшую переносимость, поскольку в этом случае поведение сервера более соответствует стандарту ISO.  
  
 Приложения на основе DB-Library обычно не вызывают включение этих параметров. Расхождения между ODBC или DB-Library клиентами под управлением той же инструкции SQL не следует рассчитывать на это указывают на проблему с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Их следует повторно выполнить инструкцию в среде DB-Library с тем же НАБОРОМ параметров, будет использовано [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента.  
  
 Поскольку пользователи и приложения могут в любое время включать и выключать параметры из набора SET, разработчики хранимых процедур и триггеров должны проводить тестирование своих процедур и триггеров как со включенными, так и с отключенными параметрами из этого набора. Это гарантирует, что триггеры и процедуры будут правильно работать независимо от того, какие параметры конкретное соединение установит при вызове триггера или процедуры. Если для работы триггера или хранимой процедуры требуется конкретное значение одного из этих параметров, инструкцию SET следует выполнить в начале триггера или хранимой процедуры. Она сохраняет силу только до завершения триггера или хранимой процедуры; после этого восстанавливается первоначальное значение параметра.  
  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливается также четвертый параметр SET, CONCAT_NULL_YIELDS_NULL. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента не устанавливает эти параметры, если значение AnsiNPW = NO указано в источнике данных или любой [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) или [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).  
  
 Как и параметры ISO, было отмечено ранее, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не включает параметр QUOTED_IDENTIFIER, если значение QuotedID = NO указано в источнике данных или любой **SQLDriverConnect** или  **SQLBrowseConnect**.  
  
 Чтобы драйвер мог узнавать текущие значения параметров SET, ODBC-приложения не должны задавать эти параметры с помощью инструкции языка [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET. Они могут задавать их только через параметры источника данных или соединения. Если приложение запускает инструкции SET, то инструкции SQL, создаваемые драйвером, могут быть неверными.  
  
## <a name="see-also"></a>См. также  
 [Выполнение инструкций &#40;ODBC&#41;](executing-statements-odbc.md)   
 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  

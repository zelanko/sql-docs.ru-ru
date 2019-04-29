---
title: Сообщения об ошибках (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b24db48d6a76c221e72944e8e5e6826cb8d5d55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127988"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Сообщения об ошибках (драйвер ODBC для Visual FoxPro)
При возникновении ошибки, Visual FoxPro драйвер возвращает следующую информацию:  
  
-   Номер собственной ошибки и текст сообщения об ошибке  
  
-   SQLSTATE (код ошибки ODBC) и текст сообщения об ошибке  
  
 Сведения об этой ошибке к путем вызова [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Собственные ошибки  
 Для ошибок, возникших в источнике данных драйвер Visual FoxPro возвращает номер собственной ошибки и текст сообщения об ошибке. Список номера собственных ошибок, см. в разделе [Visual FoxPro ODBC драйвер собственные сообщения об ошибках](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)  
 Для ошибок, обнаруженных и возвращенных драйвера для Visual FoxPro драйвер сопоставляет возвращенный собственный номер ошибки с соответствующим кодом SQLSTATE. Если собственный номер ошибки не содержит код ошибки для сопоставления с ODBC, драйвер Visual FoxPro возвращает SQLSTATE S1000 (Общая ошибка).  
  
 Список значений SQLSTATE, создаваемые драйвера ODBC для Visual FoxPro для соответствующей ошибки Visual FoxPro, см. в разделе [коды ошибок ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Синтаксис  
 Сообщения об ошибках имеют следующий формат:  
  
 **[** *поставщика* **] [** *ODBC_component* **]** *error_message*  
  
 Префиксы в квадратные скобки ([]) определить источник ошибки, как определено в таблице ниже.  
  
|Источник данных|Prefix|Значение|  
|-----------------|------------|-----------|  
|Диспетчер драйверов|[поставщик]<br />[ODBC_component]<br />[источник_данных]|[Майкрософт]<br />[Диспетчер драйверов ODBC]<br />Н/Д|  
|Драйвер Visual FoxPro|поставщика]<br />[ODBC_component]<br />[источник_данных]|[Майкрософт]<br />[ODBC Visual FoxPro driver]<br />Н/Д|  
  
 Например если драйвер ODBC для Visual FoxPro не удалось найти файл employee.dbf, может быть возвращено следующее сообщение об ошибке:  
  
 «[*Microsoft*] [*драйвера ODBC для Visual FoxPro*] файл «employee.dbf» не существует»

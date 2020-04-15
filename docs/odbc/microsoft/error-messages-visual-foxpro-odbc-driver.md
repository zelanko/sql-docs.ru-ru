---
title: Сообщения об ошибках (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31f894e58da93fe6091dba306f8b765d14bac2cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286404"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Сообщения об ошибках (драйвер ODBC для Visual FoxPro)
При возникновении ошибки водитель Visual FoxPro возвращает следующую информацию:  
  
-   Номер ошибки и текст сообщения об ошибке  
  
-   S'LSTATE (код ошибки ODBC) и текст сообщения об ошибке  
  
 Вы получаете доступ к этой информации об ошибке, позвонив по [телефону S'LError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Ошибки коренных народов  
 Для ошибок, которые возникают в источнике данных, водитель Visual FoxPro возвращает родной номер ошибки и текст сообщения об ошибке. Список родных номеров ошибок можно узнать в [Visual FoxPro ODBC Driver Native Error Messages.](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)  
 Для ошибок, обнаруженных и возвращенных драйвером Visual FoxPro, водитель отображает возвращенный номер ошибки в соответствующем номере ошибки S'Lstate. Если номер ошибки native не имеет кода ошибки ODBC для отображения, водитель Visual FoxPro возвращает S1000 (общая ошибка).  
  
 Для списка значений S'LSTATE, генерируемых Visual FoxPro ODBC Driver [ODBC Error Codes](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)для соответствующих ошибок Visual FoxPro, см.  
  
## <a name="syntax"></a>Синтаксис  
 Сообщения об ошибках имеют следующий формат:  
  
 **-** *vendor* **поставщикODBC_component** *ODBC_component* **error_message** *error_message*  
  
 Префиксы в скобках идентифицируют источник ошибки, как это определено в следующей таблице.  
  
|Источник данных|Prefix|Значение|  
|-----------------|------------|-----------|  
|Диспетчер драйверов|(поставщик)<br />(ODBC_component)<br />(data_source)|(Microsoft)<br />(менеджер драйвера ODBC)<br />Н/Д|  
|Визуальный драйвер FoxPro|поставщик<br />(ODBC_component)<br />(data_source)|(Microsoft)<br />(водитель ODBC Visual FoxPro)<br />Н/Д|  
  
 Например, если водитель Visual FoxPro ODBC не смог найти файл employee.dbf, он может вернуть следующее сообщение об ошибке:  
  
 «У*Microsoft**ODBC Visual FoxPro Driver*»Файл 'employee.dbf' не существует»

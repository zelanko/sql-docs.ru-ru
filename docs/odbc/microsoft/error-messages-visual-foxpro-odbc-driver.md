---
title: Сообщения об ошибках (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4f6be0c46b1dcc777004edacda8a490438db438c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Сообщения об ошибках (драйвер ODBC для Visual FoxPro)
При возникновении ошибки в драйвере Visual FoxPro возвращает следующую информацию:  
  
-   Номер собственной ошибки и текст сообщения об ошибке  
  
-   SQLSTATE (код ошибки ODBC) и текст сообщения об ошибке  
  
 Сведения об этой ошибке к путем вызова [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Собственные ошибки  
 Для ошибок, возникающих в источнике данных драйвер Visual FoxPro возвращает номер собственной ошибки и текст сообщения об ошибке. Список номера собственных ошибок см. в разделе [Visual FoxPro ODBC Driver собственные сообщения об ошибках](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)  
 Для ошибок, обнаруживаются и возвращаемых драйвером Visual FoxPro драйвер сопоставляет возвращенный собственный номер ошибки с соответствующим кодом SQLSTATE. Если номер собственной ошибки не имеет код ошибки ODBC для сопоставления, Visual FoxPro драйвер возвращает SQLSTATE S1000 (ошибка).  
  
 Список значения SQLSTATE, созданные Visual FoxPro драйвер ODBC для соответствующих ошибок Visual FoxPro см. в разделе [коды ошибок ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Синтаксис  
 Сообщения об ошибках имеют следующий формат:  
  
 **[** *поставщика* **] [** *ODBC_component* **]** *error_message*  
  
 Префиксы в квадратные скобки ([]) определить источник ошибки, как определено в таблице ниже.  
  
|Источник данных|Prefix|Значение|  
|-----------------|------------|-----------|  
|Диспетчер драйверов|[поставщик]<br />[ODBC_component]<br />[источник_данных]|[Microsoft]<br />[Диспетчер драйверов ODBC]<br />Недоступно|  
|Драйвер Visual FoxPro|Поставщик]<br />[ODBC_component]<br />[источник_данных]|[Microsoft]<br />[Драйвер ODBC Visual FoxPro]<br />Недоступно|  
  
 Например если драйвер ODBC для Visual FoxPro не удалось найти файл employee.dbf, могут возвращать сообщение об ошибке:  
  
 «[*Microsoft*] [*драйвера ODBC для Visual FoxPro*] файл «employee.dbf» не существует»

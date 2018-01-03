---
title: "Сообщения об ошибках (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ec1cbc18c952c4394f16123c76a32330116d5af
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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

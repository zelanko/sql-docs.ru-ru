---
title: "SQLSetConnectOption (драйвер доступа) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b8f7497cb6b36602908443ab4fd9bdeb592ce8af
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (драйвер доступа)
> [!NOTE]  
>  В этом разделе сведения драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption можно присвоить значение SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Тем не менее драйвер не запрещает обновление, если SQL_ACCESS_MODE равно SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Когда используется драйвер Microsoft Access, параметр SQL_AUTOCOMMIT может быть присвоено SQL_AUTOCOMMIT_ON или SQL_AUTOCOMMIT_OFF, так как драйвер Microsoft Access поддерживает транзакции [1].|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION всегда является SQL_TXN_READ_COMMITTED.|  
  
 [1] атомарные транзакции не поддерживается драйвером Microsoft Access. При фиксации транзакции с помощью драйвера Microsoft Access, конечное задержки существует между времени, транзакция завершается и значения записываются на диск. Эта задержка определяется задержки, встроенные в ядро Microsoft Jet. Время ожидания страницы не будет меньше, чем минимальное значение, даже если параметр PageTimeout имеет значение ниже этого значения. Как следствие, нет никакой гарантии, что зафиксированные данные стабильна, так как во время задержки могут быть внесены изменения.

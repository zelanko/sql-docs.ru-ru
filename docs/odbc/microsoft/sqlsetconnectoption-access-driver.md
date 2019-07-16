---
title: SQLSetConnectOption (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bea124a78e2a180180c59de3577fe1db7637e110
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67897788"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Можно задать SQL_ACCESS_MODE fOption SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Тем не менее драйвер не запрещает обновление, если задано значение SQL_ACCESS_MODE SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Когда используется драйвером Microsoft Access, параметр SQL_AUTOCOMMIT может задаваться к SQL_AUTOCOMMIT_OFF, либо параметром SQL_AUTOCOMMIT_ON, поскольку драйвером Microsoft Access поддерживает транзакции [1].|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION всегда является SQL_TXN_READ_COMMITTED.|  
  
 [1] атомарные транзакции не поддерживается драйвером Microsoft Access. Существует при фиксации транзакции с помощью драйвера Microsoft Access, конечное задержка между временем, транзакция фиксируется и времени, значения записываются на диск. Эта задержка определяется задержка, встроенные в ядро Microsoft Jet. Время ожидания страницы не будет меньше, чем минимальное значение, даже если параметр PageTimeout имеет значение ниже этого значения. Таким образом, нет никакой гарантии, что зафиксированные данные стабильна, так как во время задержки могут вноситься изменения.

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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67897788"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Параметром fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE параметром fOption можно задать как SQL_MODE_READ_ONLY, так и SQL_MODE_READ_WRITE. Однако драйвер не запрещает обновление, если для SQL_ACCESS_MODE установлено значение SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|При использовании драйвера Microsoft Access параметру SQL_AUTOCOMMIT может быть присвоено значение SQL_AUTOCOMMIT_ON или SQL_AUTOCOMMIT_OFF, поскольку драйвер Microsoft Access поддерживает транзакции [1].|  
|SQL_CURRENT_QUALIFIER| Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE| Поддерживается.|  
|SQL_OPT_TRACEFILE| Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION всегда SQL_TXN_READ_COMMITTED.|  
  
 [1] неатомарные транзакции не поддерживаются драйвером Microsoft Access. При фиксации транзакции с помощью драйвера Microsoft Access существует конечная задержка между временем фиксации транзакции и записью значений на диск. Эта задержка определяется задержкой, присущей ядру Microsoft Jet. Время ожидания страницы не будет меньше минимального значения, даже если параметр Пажетимеаут задан ниже этого значения. В результате нет никакой гарантии, что зафиксированные данные будут стабильными, так как изменения могут быть сделаны во время задержки.

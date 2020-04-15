---
title: СЗЛСТоУкНоукВариант (Водитель Excel) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Excel Driver
- Excel driver [ODBC], SQLSetConnectOption
ms.assetid: 528d21d1-4516-4497-9da4-7b87d77e622a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b9ddd764823b4ed89d9aae7055cf966f9f840a3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301515"
---
# <a name="sqlsetconnectoption-excel-driver"></a>SQLSetConnectOption (драйвер для Excel)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах Excel. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|fOption|Комментарий|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption можно установить на SQL_MODE_READ_ONLY или SQL_MODE_READ_WRITE. Однако драйвер не препятствует обновлению, если SQL_ACCESS_MODE настроена на SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Драйвер Microsoft Excel поддерживает только SQL_AUTOCOMMIT, устанавливаемых в ON (состояние по умолчанию), поскольку они не поддерживают транзакции.|  
|SQL_CURRENT_QUALIFIER|Поддерживается.|  
|SQL_LOGIN_TIMEOUT|Не поддерживается.|  
|SQL_OPT_TRACE|Поддерживается.|  
|SQL_OPT_TRACEFILE|Поддерживается.|  
|SQL_PACKET_SIZE|Не поддерживается.|  
|SQL_QUIET_MODE|Не поддерживается.|  
|SQL_TRANSLATE_DLL|Не поддерживается.|  
|SQL_TRANSLATION_OPTION|Не поддерживается.|  
|SQL_TXN_ISOLATION|Не поддерживается.|

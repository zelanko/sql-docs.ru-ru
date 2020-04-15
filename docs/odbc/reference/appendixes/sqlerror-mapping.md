---
title: СЗЛОшибка Картпинг (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1aa3b66b29af755099cb273f3a19ca4e8230cd0b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302083"
---
# <a name="sqlerror-mapping"></a>Сопоставление SQLError
Когда приложение вызывает **S'LError** через драйвер ODBC *3.x,*  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 отображается до  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 с *аргументом HandleType,* установленным на значение SQL_HANDLE_ENV, SQL_HANDLE_DBC или SQL_HANDLE_STMT, по мере необходимости, и аргумент *ручки,* установленный на значение в *henv,* *hdbc*, или *hstmt*, по мере необходимости. Аргумент *RecNumber* определяется менеджером драйвера.

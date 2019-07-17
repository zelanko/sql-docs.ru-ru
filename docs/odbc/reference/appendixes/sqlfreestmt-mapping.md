---
title: Сопоставление SQLFreeStmt | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a92af35d8a1b1e98a484c69d7d2e66bf5bef3196
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086078"
---
# <a name="sqlfreestmt-mapping"></a>Сопоставление SQLFreeStmt
Если приложение вызывает **SQLFreeStmt** с *параметр* аргумент SQL_DROP через ODBC *3.x* драйвера, вызов метода  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 сопоставляется с  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 с помощью *обрабатывать* аргументу присвоено значение в *hstmt*.

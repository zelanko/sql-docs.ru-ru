---
title: Картирование S'LFreeStmt Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9d187db4d40132385b9ae4564fddbf89987e3e97
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302015"
---
# <a name="sqlfreestmt-mapping"></a>Сопоставление SQLFreeStmt
Когда приложение вызывает **S'LFreeStmt** с аргументом *опции* SQL_DROP через драйвер ODBC *3.x,* вызов  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 отображается до  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 с *аргументом Ручка* установлен к значению в *hstmt.*

---
title: "Сопоставление SQLAllocEnv | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1061472d46a49ca105fb970b19a2f2d950470a12
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlallocenv-mapping"></a>Сопоставление SQLAllocEnv
Если приложение вызывает **SQLAllocEnv** через ODBC 3*.x* драйвера, вызов **SQLAllocEnv**(*phenv*) сопоставляется с **SQLAllocHandle** следующим образом:  
  
1.  Диспетчер драйверов выделяет дескриптор среды и возвращает его в приложение. Диспетчер драйверов вызывает **SQLSetEnvAttr** для задания атрибута среды SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Вызывается, когда приложение устанавливает первого подключения к драйверу, диспетчер драйверов  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     в драйвере с *OutputHandlePtr* значение *phenv*.

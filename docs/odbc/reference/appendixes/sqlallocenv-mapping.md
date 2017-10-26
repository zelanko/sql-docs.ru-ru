---
title: "Сопоставление SQLAllocEnv | Документы Microsoft"
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
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 66261c8fd8236a4abc35ac70e29f63b49f646daf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocenv-mapping"></a>Сопоставление SQLAllocEnv
Если приложение вызывает **SQLAllocEnv** через ODBC 3*.x* драйвера, вызов **SQLAllocEnv**(*phenv*) сопоставляется с **SQLAllocHandle** следующим образом:  
  
1.  Диспетчер драйверов выделяет дескриптор среды и возвращает его в приложение. Диспетчер драйверов вызывает **SQLSetEnvAttr** для задания атрибута среды SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Вызывается, когда приложение устанавливает первого подключения к драйверу, диспетчер драйверов  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     в драйвере с *OutputHandlePtr* значение *phenv*.


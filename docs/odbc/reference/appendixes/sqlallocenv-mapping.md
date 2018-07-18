---
title: Сопоставление SQLAllocEnv | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ca05f911091bd3c18641371281f3ac4b1372063
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907069"
---
# <a name="sqlallocenv-mapping"></a>Сопоставление SQLAllocEnv
Если приложение вызывает **SQLAllocEnv** через ODBC 3 *.x* драйвера, вызов **SQLAllocEnv**(*phenv*) сопоставляется с **SQLAllocHandle** следующим образом:  
  
1.  Диспетчер драйверов выделяет дескриптор среды и возвращает его в приложение. Диспетчер драйверов вызывает **SQLSetEnvAttr** для задания атрибута среды SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Вызывается, когда приложение устанавливает первого подключения к драйверу, диспетчер драйверов  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     в драйвере с *OutputHandlePtr* значение *phenv*.

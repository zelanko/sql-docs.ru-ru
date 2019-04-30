---
title: Сопоставление SQLAllocEnv | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39736d4d007814e29bc8c8293fa7e1020539b940
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280861"
---
# <a name="sqlallocenv-mapping"></a>Сопоставление SQLAllocEnv
Если приложение вызывает **SQLAllocEnv** через ODBC 3 *.x* драйвера, вызов **SQLAllocEnv**(*phenv*) сопоставляется с **SQLAllocHandle** следующим образом:  
  
1.  Диспетчер драйверов выделяет дескриптор среды и возвращает его приложению. Диспетчер драйверов вызывает **SQLSetEnvAttr** присвоить атрибуту окружения SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Когда приложение устанавливает первого подключения к драйверу, диспетчер драйверов вызывает  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     в драйвере с *OutputHandlePtr* присвоено *phenv*.

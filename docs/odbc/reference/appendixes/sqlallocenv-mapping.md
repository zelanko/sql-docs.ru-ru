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
ms.openlocfilehash: afbd1404cb40408166ecfc59993db7b183ae5ed2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065009"
---
# <a name="sqlallocenv-mapping"></a>Сопоставление SQLAllocEnv
Когда приложение вызывает **SQLAllocEnv** через драйвер ODBC *3. x* , вызов **SQLAllocEnv**(*фенв*) сопоставляется с **функцию SQLAllocHandle** следующим образом:  
  
1.  Диспетчер драйверов выделяет маркер среды и возвращает его приложению. Диспетчер драйверов вызывает **SQLSetEnvAttr** , чтобы задать SQL_OV_ODBC2 атрибута среды SQL_ATTR_ODBC_VERSION.  
  
2.  Когда приложение устанавливает первое подключение к драйверу, диспетчер драйверов вызывает  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     в драйвере с параметром *аутпусандлептр* задано значение *фенв*.

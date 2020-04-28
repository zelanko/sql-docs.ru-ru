---
title: Сопоставление SQLAllocConnect | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25e72cd3830cea8504983f4348f6c200261490f4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305525"
---
# <a name="sqlallocconnect-mapping"></a>Сопоставление SQLAllocConnect
Когда приложение вызывает **SQLAllocConnect** через ODBC 3. драйвер *x* , вызов **SQLAllocConnect**(*хенв*, *фдбк*) сопоставляется с **функцию SQLAllocHandle** следующим образом:  
  
1.  Диспетчер драйверов выделяет соединение и возвращает его приложению.  
  
2.  Когда приложение устанавливает соединение, диспетчер драйверов вызывает метод  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     в драйвере с параметром *инпусандле* установлено значение *хенв*, а для *аутпусандлептр* — значение *фдбк*.

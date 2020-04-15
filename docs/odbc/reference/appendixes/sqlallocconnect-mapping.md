---
title: Картирование s'LAllocConnect (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305525"
---
# <a name="sqlallocconnect-mapping"></a>Сопоставление SQLAllocConnect
Когда приложение вызывает **S'LAllocConnect** через ODBC 3. *х* драйвер, вызов на **S'LAllocConnect**(*henv*, *phdbc*) отображается на **S'LAllocHandle** следующим образом:  
  
1.  Менеджер драйвера выделяет соединение и возвращает его в приложение.  
  
2.  Когда приложение устанавливает соединение, менеджер драйвера вызывает  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     в драйвере с *InputHandle* набор *henv*, и *OutputHandlePtr* установить *на phdbc*.

---
title: "Библиотеки DLL настройки транслятора | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc2fa42c2535d794dcf93160bf79b71d8c226640
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="translator-setup-dlls"></a>Транслятор установки DLL-библиотеки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 DLL-Библиотека содержит настройки транслятора **ConfigTranslator** функции, которая возвращает параметр по умолчанию для преобразователя. При необходимости, то выводит запрос для получения этих сведений. Полное описание этой функции см. в разделе [Справочник по API библиотеки DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Настройка транслятора разработчиком переводчик записывается DLL. Он может быть частью транслятор DLL или отдельную библиотеку DLL.


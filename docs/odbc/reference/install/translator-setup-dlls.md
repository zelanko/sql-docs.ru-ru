---
title: "Библиотеки DLL настройки транслятора | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ce6961ec470bf0e0a7281a129d85f5cf69c9b80
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="translator-setup-dlls"></a>Транслятор установки DLL-библиотеки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 DLL-Библиотека содержит настройки транслятора **ConfigTranslator** функции, которая возвращает параметр по умолчанию для преобразователя. При необходимости, то выводит запрос для получения этих сведений. Полное описание этой функции см. в разделе [Справочник по API библиотеки DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Настройка транслятора разработчиком переводчик записывается DLL. Он может быть частью транслятор DLL или отдельную библиотеку DLL.

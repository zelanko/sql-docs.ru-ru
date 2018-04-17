---
title: Библиотеки DLL настройки транслятора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4974722410319634e6bc4c18fd8bdea7d89c9cb1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="translator-setup-dlls"></a>Транслятор установки DLL-библиотеки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 DLL-Библиотека содержит настройки транслятора **ConfigTranslator** функции, которая возвращает параметр по умолчанию для преобразователя. При необходимости, то выводит запрос для получения этих сведений. Полное описание этой функции см. в разделе [Справочник по API библиотеки DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Настройка транслятора разработчиком переводчик записывается DLL. Он может быть частью транслятор DLL или отдельную библиотеку DLL.

---
title: Библиотеки DLL настройки транслятора | Документы Microsoft
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
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65eca03533940a50a169a948021342f71a032153
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="translator-setup-dlls"></a>Транслятор установки DLL-библиотеки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 DLL-Библиотека содержит настройки транслятора **ConfigTranslator** функции, которая возвращает параметр по умолчанию для преобразователя. При необходимости, то выводит запрос для получения этих сведений. Полное описание этой функции см. в разделе [Справочник по API библиотеки DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Настройка транслятора разработчиком переводчик записывается DLL. Он может быть частью транслятор DLL или отдельную библиотеку DLL.

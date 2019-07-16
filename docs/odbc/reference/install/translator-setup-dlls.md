---
title: Библиотеки DLL программы установки Translator | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b6c99dffc94f2675efdbbc3d5c1d142a5ae9b7e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093841"
---
# <a name="translator-setup-dlls"></a>Библиотеки DLL программы установки преобразователя
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включена в операционную систему Windows. ODBC следует только явным образом установить в более ранних версиях Windows.  
  
 Программа установки translator, DLL-Библиотека содержит **ConfigTranslator** функции, которая возвращает параметр по умолчанию для переводчика. При необходимости запрашивает у пользователя эти сведения. Полное описание этой функции, см. в разделе [Справочник по API библиотеки DLL программы установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Настройка translator DLL записывается разработчиком translator. Он может быть частью переводчик DLL или отдельный файл DLL.

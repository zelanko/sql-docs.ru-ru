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
manager: craigg
ms.openlocfilehash: 20453b792ed00b388977fefe3064fd8dfca86147
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610132"
---
# <a name="translator-setup-dlls"></a>Библиотеки DLL программы установки преобразователя
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включена в операционную систему Windows. ODBC следует только явным образом установить в более ранних версиях Windows.  
  
 Программа установки translator, DLL-Библиотека содержит **ConfigTranslator** функции, которая возвращает параметр по умолчанию для переводчика. При необходимости запрашивает у пользователя эти сведения. Полное описание этой функции, см. в разделе [Справочник по API библиотеки DLL программы установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Настройка translator DLL записывается разработчиком translator. Он может быть частью переводчик DLL или отдельный файл DLL.

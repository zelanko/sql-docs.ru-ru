---
description: Библиотеки DLL программы установки преобразователя
title: Библиотеки DLL установки переводчиков | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2fe4d514f098773024392666d8f528592d362da4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487397"
---
# <a name="translator-setup-dlls"></a>Библиотеки DLL программы установки преобразователя
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Библиотека DLL установки транслятора содержит функцию **конфигтранслатор** , которая возвращает параметр по умолчанию для транслятора. При необходимости он запрашивает у пользователя эти сведения. Полное описание этой функции см. в [справочнике по API DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Библиотека DLL установки переводчиков записывается разработчиком переводчика. Он может быть частью библиотеки DLL транслятора или отдельной библиотекой DLL.

---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b6c99dffc94f2675efdbbc3d5c1d142a5ae9b7e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093841"
---
# <a name="translator-setup-dlls"></a>Библиотеки DLL программы установки преобразователя
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Библиотека DLL установки транслятора содержит функцию **конфигтранслатор** , которая возвращает параметр по умолчанию для транслятора. При необходимости он запрашивает у пользователя эти сведения. Полное описание этой функции см. в [справочнике по API DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Библиотека DLL установки переводчиков записывается разработчиком переводчика. Он может быть частью библиотеки DLL транслятора или отдельной библиотекой DLL.

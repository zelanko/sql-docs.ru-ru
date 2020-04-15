---
title: Настройка переводчика DLLs (ru) Документы Майкрософт
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
ms.openlocfilehash: 28c354fddb36b9e035361fa4ba03fbde34b7d399
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296054"
---
# <a name="translator-setup-dlls"></a>Библиотеки DLL программы установки преобразователя
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включен в систему работы Windows. Вы должны только явно установить ODBC на более ранних версиях Windows.  
  
 Настройка DLL переводчика содержит функцию **ConfigTranslator,** которая возвращает опцию по умолчанию для переводчика. При необходимости он подсказывает пользователю эту информацию. Для полного описания этой [Setup DLL API Reference](../../../odbc/reference/syntax/setup-dll-api-reference.md)функции см.  
  
 Настройка переводчика DLL написана разработчиком переводчика. Она может быть частью переводчика DLL или отдельного DLL.

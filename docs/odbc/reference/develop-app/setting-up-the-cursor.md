---
title: Настройка курсора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59ade343f282933e05619996b119bc08e2dfb2ab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825522"
---
# <a name="setting-up-the-cursor"></a>Настройка курсора
Приложение может задать тип курсора, прежде чем выполнение инструкцию, которая создает результирующий набор. Это делается с помощью атрибута SQL_ATTR_CURSOR_TYPE инструкции. Если приложение явно не задает тип, будет использоваться однопроходный курсор. Чтобы получить смешанной курсора, приложение указывает курсор, управляемый набором ключей, но объявляет размер набора ключей, меньше, чем размер набора результатов.  
  
 Для курсоров, управляемых набором ключей и смешанного приложение также можно указать размер набора ключей. Это делается с помощью атрибута SQL_ATTR_KEYSET_SIZE атрибут инструкции. Если размер набора ключей имеет значение 0, который используется по умолчанию, размер набора ключей имеет значение размера результирующего набора, и используется курсор, управляемый набором ключей. Размер набора ключей может изменяться после открытия курсора.  
  
 Приложение также может задать размер набора строк; Дополнительные сведения см. в разделе [использование блочных курсоров](../../../odbc/reference/develop-app/using-block-cursors.md)ранее в этом разделе.

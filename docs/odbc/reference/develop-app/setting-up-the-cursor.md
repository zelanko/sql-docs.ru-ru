---
title: Настройка Курсора Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 805d8076c853513d86f9a3a92d9342d1224226c9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299804"
---
# <a name="setting-up-the-cursor"></a>Настройка курсора
Приложение может указать тип курсора перед выполнением оператора, создающего набор результатов. Он делает это с атрибутом SQL_ATTR_CURSOR_TYPE оператора. Если приложение явно не указывает тип, будет использоваться курсор только для форварда. Чтобы получить смешанный курсор, приложение определяет курсор, управляемый клавиатурой, но объявляет размер ключа меньше, чем размер набора результата.  
  
 Для клавиатурных и смешанных курсоров приложение также может указать размер набора ключей. Он делает это с атрибутом SQL_ATTR_KEYSET_SIZE оператора. Если размер ключа установлен до 0, то есть по умолчанию, размер набора ключей устанавливается на размер набора результата и используется курсор, управляемый клавиатурой. Размер ключа может быть изменен после открытия курсора.  
  
 Приложение также может установить размер рядового набора; для получения дополнительной информации, [см. Использование блок-курсоров](../../../odbc/reference/develop-app/using-block-cursors.md), ранее в этом разделе.

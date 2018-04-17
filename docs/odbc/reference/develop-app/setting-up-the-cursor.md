---
title: Настройка курсор | Документы Microsoft
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
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39bb6f6f61d8477fae1f0a07b2960b77dd987643
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-the-cursor"></a>Настройка курсора
Приложения можно указать тип курсора до выполнения инструкции, которая создает результирующий набор. Это делается с помощью атрибута SQL_ATTR_CURSOR_TYPE инструкции. Если приложение явно не указан тип, будет использоваться однонаправленный курсор. Для получения смешанного курсора, приложение указывает курсор, управляемый набором ключей, но объявляет размер набора ключей, меньше, чем размер набора результатов.  
  
 Для курсоров, управляемых набором ключей, так и приложение можно также указать размер набора ключей. Это делается с помощью атрибута SQL_ATTR_KEYSET_SIZE атрибута инструкции. Если размер набора ключей равно 0, то есть значение по умолчанию, размер набора ключей равно размер результирующего набора и используется курсор, управляемый набором ключей. Размер ключей можно изменить после открытия курсора.  
  
 Приложение также можно задать размер набора строк; Дополнительные сведения см. в разделе [использование блочных курсоров](../../../odbc/reference/develop-app/using-block-cursors.md)ранее в этом разделе.

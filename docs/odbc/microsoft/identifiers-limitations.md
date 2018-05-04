---
title: Идентификаторы ограничения | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 591404db64ec5969b1236c318984191caea3a2cd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="identifiers-limitations"></a>Идентификаторы ограничений
Если идентификатор содержит пробел или специальных символов, идентификатор должны заключаться в кавычки назад. Допустимое имя является строкой, не более 64 символов, в которых первый символ не должен быть пробел. Допустимые имена не может содержать управляющие символы или следующие специальные символы: " &#124; # *? [ ] . ! $ .  
  
 Не используйте зарезервированные слова, перечисленные в грамматику SQL в приложении С *справочнике программиста ODBC* (или краткая форма эти зарезервированные слова) как идентификаторы (то есть имена таблиц или столбцов), если не заключить слово назад кавычки (').

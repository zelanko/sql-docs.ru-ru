---
title: Ограничения идентификаторов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c781113124d456e1ba866546d6ada7a17371d71f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208530"
---
# <a name="identifiers-limitations"></a>Ограничения идентификаторов
Если идентификатор содержит пробел или специальный символ, идентификатор должны заключаться в кавычки назад. Допустимое имя является строкой, не более 64 символов, в которых первый символ не должен быть пробел. Допустимые имена не может содержать управляющие символы или следующие специальные символы: " &#124; # *? [ ] . ! $ .  
  
 Не используйте зарезервированные слова, перечисленные в грамматике SQL в приложении С *Справочник по программированию ODBC* (или краткая форма эти зарезервированные слова) как идентификаторы (то есть имена таблиц или столбцов), если не заключить слово назад кавычки (').

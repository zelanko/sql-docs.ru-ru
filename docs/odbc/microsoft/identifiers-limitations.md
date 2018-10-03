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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667392"
---
# <a name="identifiers-limitations"></a>Ограничения идентификаторов
Если идентификатор содержит пробел или специальный символ, идентификатор должны заключаться в кавычки назад. Допустимое имя является строкой, не более 64 символов, в которых первый символ не должен быть пробел. Допустимые имена не может содержать управляющие символы или следующие специальные символы: " &#124; # *? [ ] . ! $ .  
  
 Не используйте зарезервированные слова, перечисленные в грамматике SQL в приложении С *Справочник по программированию ODBC* (или краткая форма эти зарезервированные слова) как идентификаторы (то есть имена таблиц или столбцов), если не заключить слово назад кавычки (').

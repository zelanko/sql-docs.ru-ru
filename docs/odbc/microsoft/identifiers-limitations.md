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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7154f2db09b69e6376b1fe3af1de3f2c646ee94e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286254"
---
# <a name="identifiers-limitations"></a>Ограничения идентификаторов
Если идентификатор содержит пробел или специальный символ, идентификатор должен быть заключен в обратные кавычки. Допустимое имя — это строка, в которой не более 64 символов, первый символ не должен быть пробелом. Допустимые имена не могут содержать управляющие символы или следующие специальные символы: "&#124; # *? [ ] . ! $ .  
  
 Не используйте зарезервированные слова, перечисленные в грамматике SQL в приложении C *Справочника программиста ODBC* (или сокращенной формы этих зарезервированных слов) в качестве идентификаторов (т. е. имен таблиц или столбцов), если слова не заключены в обратные кавычки (').

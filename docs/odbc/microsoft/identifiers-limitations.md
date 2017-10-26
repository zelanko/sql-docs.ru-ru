---
title: "Идентификаторы ограничения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ec32697030d2ad4ede765879f83956692ed49914
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="identifiers-limitations"></a>Идентификаторы ограничений
Если идентификатор содержит пробел или специальных символов, идентификатор должны заключаться в кавычки назад. Допустимое имя является строкой, не более 64 символов, в которых первый символ не должен быть пробел. Допустимые имена не может содержать управляющие символы или следующие специальные символы: "&#124; # * ? [ ] . ! $ .  
  
 Не используйте зарезервированные слова, перечисленные в грамматику SQL в приложении С *справочнике программиста ODBC* (или краткая форма эти зарезервированные слова) как идентификаторы (то есть имена таблиц или столбцов), если не заключить слово назад кавычки (').


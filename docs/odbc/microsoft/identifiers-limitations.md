---
title: Ограничения идентификаторов Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286254"
---
# <a name="identifiers-limitations"></a>Ограничения идентификаторов
Если идентификатор содержит пробел или специальный символ, идентификатор должен быть заключен в задние кавычки. Действительное имя представляет собой строку из не более 64 символов, из которых первый символ не должен быть пространством. Действительные имена не могут включать контрольные символы или следующие специальные символы: '&#124; ? [ ] . ! $ .  
  
 Не используйте зарезервированные слова, перечисленные в грамматике СЗЛ, в приложении C *Справочника программиста ODBC* (или краткой форме этих зарезервированных слов) в качестве идентификаторов (т.е. названий таблицы или столбца), если только вы не окружаете слово в задних кавычках (').

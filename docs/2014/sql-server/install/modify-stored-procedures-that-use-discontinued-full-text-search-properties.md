---
title: Измените хранимые процедуры, в которых используются неподдерживаемые свойства полнотекстового поиска | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 027fb2a7148dc0948c519836f30c8931d61f610b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099728"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a>Измените хранимые процедуры, в которых используются неподдерживаемые свойства полнотекстового поиска
  Чтобы обеспечить правильную работу хранимых процедур, нужно изменить существующие процедуры, удалив свойства и настройки, связанные с полнотекстовым поиском, которые были удалены или устарели.  
  
## <a name="component"></a>Компонент  
 Компонент Full-text Search  
  
## <a name="description"></a>Описание  
 Следующие свойства и настройки, связанные с полнотекстовым поиском, были удалены.  
  
-   **DataTimeout**  
  
-   **ConnectTimeout**  
  
-   **Clean_up**  
  
-   **LogSize**  
  
 Следующие свойства и настройки, связанные с полнотекстовым поиском, были удалены или устарели.  
  
-   Параметр Path полнотекстового каталога. Полнотекстовый каталог будет логическим объектом, не имеющим конкретного файлового пути.  
  
-   Включение или отключение полнотекстового поиска с помощью процедуры SP_FULLTEXT_DATABASE больше не работает, так как в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] базы данных по умолчанию всегда доступны для полнотекстового поиска.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените хранимые процедуры, чтобы удалить эти свойства.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
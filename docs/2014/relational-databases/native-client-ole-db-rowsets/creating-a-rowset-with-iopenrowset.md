---
title: Создание набора строк с IOpenRowset | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7cdce7632aa726d2992a0383d19691569ed57c0a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194924"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Создание набора строк с помощью интерфейса IOpenRowset
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поддерживает поставщик OLE DB для собственного клиента **IOpenRowset::OpenRowset** метод со следующими ограничениями:  
  
-   Базовая таблица или представление должен быть указан в базе данных (DBID) идентификатор структуру, в которой *pTableID* указывает параметр.  
  
-   DBID *eKind* член должен указывать DBKIND_NAME.  
  
-   DBID *uName* элемента необходимо указать имя существующей базовой таблицы или представления, как строку символов Юникода.  
  
-   *PIndexID* параметр **OpenRowset** должен иметь значение NULL.  
  
 Результирующий набор **IOpenRowset::OpenRowset** содержит единственный набор строк. Результирующие наборы, содержащие единственный набор строк может поддерживаться [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров. Благодаря поддержке курсоров разработчик может использовать механизмы параллелизма [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  
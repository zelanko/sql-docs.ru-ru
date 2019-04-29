---
title: Создание набора строк с помощью интерфейса IOpenRowset | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4aa7b91b10c2ce266ad648bce0ba1c19946098c8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63183708"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Создание набора строк с помощью интерфейса IOpenRowset
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поддерживает поставщик OLE DB для собственного клиента **IOpenRowset::OpenRowset** метод со следующими ограничениями:  
  
-   Базовая таблица или представление должны быть определены в структуре идентификатора базы данных (DBID), на которую указывает параметр *pTableID*.  
  
-   Член DBID *eKind* должен указывать DBKIND_NAME.  
  
-   Член DBID *uName* должен содержать имя существующей базовой таблицы или представления в виде строки в Юникоде.  
  
-   Параметр *pIndexID* компонента **OpenRowset** должен иметь значение NULL.  
  
 Результирующий набор интерфейса **IOpenRowset::OpenRowset** содержит один набор строк. Результирующие наборы, содержащие по одному набору строк, могут поддерживаться курсорами [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Благодаря поддержке курсоров разработчик может использовать механизмы параллелизма [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  

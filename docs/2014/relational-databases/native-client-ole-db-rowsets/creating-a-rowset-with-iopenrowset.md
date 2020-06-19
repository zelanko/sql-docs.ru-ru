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
author: rothja
ms.author: jroth
ms.openlocfilehash: bf74466a698d39f74b9531adaa54c79c75e50ef2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055987"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Создание набора строк с помощью интерфейса IOpenRowset
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB Native Client поддерживает метод **IOpenRowset:: OPENROWSET** со следующими ограничениями:  
  
-   Базовая таблица или представление должны быть определены в структуре идентификатора базы данных (DBID), на которую указывает параметр *pTableID*.  
  
-   Член DBID *eKind* должен указывать DBKIND_NAME.  
  
-   Член DBID *uName* должен содержать имя существующей базовой таблицы или представления в виде строки в Юникоде.  
  
-   Параметр *pIndexID* компонента **OpenRowset** должен иметь значение NULL.  
  
 Результирующий набор интерфейса **IOpenRowset::OpenRowset** содержит один набор строк. Результирующие наборы, содержащие один набор строк, могут поддерживаться [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсорами. Благодаря поддержке курсоров разработчик может использовать механизмы параллелизма [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](rowsets.md)  
  
  

---
title: Удаление таблицы SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- SQL Server Native Client OLE DB provider, tables
- removing tables
- dropping tables
ms.assetid: b6d6c4de-43c6-473e-92aa-34ffddd58cbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d7bea98a3afcd0022f66117b6bde2d968a866b7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85017988"
---
# <a name="dropping-a-sql-server-table"></a>Удаление таблицы SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DBа собственного клиента предоставляет функцию **ITableDefinition::D роптабле** . Это позволяет пользователям удалять [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы из базы данных.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Таблицы и индексы](tables-and-indexes.md)  
  
  

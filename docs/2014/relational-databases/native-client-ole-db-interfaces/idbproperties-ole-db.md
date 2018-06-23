---
title: IDBProperties (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3bee573d18bce37685612ab79a715834ca27e5fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109488"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  Стандартная спецификация OLE DB допускает задание поставщиками VT_EMPTY для `DBPROPINFO::vValues`. Тем не менее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента всегда возвращает VT_EMPTY при вызове `IDBProperties::GetPropertyInfo` с `DBPROPSET_ROWSETALL` для извлечения свойств набора строк.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
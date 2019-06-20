---
title: IDBProperties (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b6dada26e15fc83d890b270ad553eb051bb08fa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62692182"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  Стандартная спецификация OLE DB допускает задание поставщиками VT_EMPTY для `DBPROPINFO::vValues`. Тем не менее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента всегда возвращает VT_EMPTY при вызове `IDBProperties::GetPropertyInfo` с `DBPROPSET_ROWSETALL` для извлечения свойств набора строк.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  

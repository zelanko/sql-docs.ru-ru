---
title: IDBProperties (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7598f1c865395f2a43eba8f67c86a68bd46d586b
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707366"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  Стандартная спецификация OLE DB допускает задание поставщиками VT_EMPTY для `DBPROPINFO::vValues`. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DB всегда возвращает VT_EMPTY при вызове `IDBProperties::GetPropertyInfo` с помощью `DBPROPSET_ROWSETALL` для получения свойств набора строк.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (OLE DB)](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  

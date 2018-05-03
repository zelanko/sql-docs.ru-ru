---
title: Свойство поставщика (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 412a54f0a8028e14533a7e5bcb6a16f1911bcf14
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="provider-property-ado"></a>Свойство поставщика (ADO)
Указывает имя поставщика для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, указывающее имя поставщика.  
  
## <a name="remarks"></a>Замечания  
 Используйте **поставщика** свойство задает или возвращает имя поставщика для подключения. Это свойство можно также задать по содержимому [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство или *ConnectionString* аргумент [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод; Однако Указание поставщика в более чем в одном месте при вызове **откройте** метода может привести к непредсказуемым результатам. Если поставщик не указан, свойство по умолчанию MSDASQL ([поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 **Поставщика** свойство является чтение и запись, когда подключение закрыто, только для чтения при открытом. Параметр вступает в силу только после откройте **подключения** объекта или доступа [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию **подключения** объекта. Если параметр не является допустимым, возвращается ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Поставщик и пример использования свойств DefaultDatabase (Visual Basic)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Поставщик и пример использования свойств DefaultDatabase (Visual Basic)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)

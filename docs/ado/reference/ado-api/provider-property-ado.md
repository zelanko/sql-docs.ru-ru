---
title: Свойство Provider (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fae46773befb13105ed9dcd81b1116be48cf0675
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931451"
---
# <a name="provider-property-ado"></a>Свойство Provider (ADO)
Указывает имя поставщика для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, указывающее имя поставщика.  
  
## <a name="remarks"></a>Примечания  
 Используйте **поставщика** свойство задает или возвращает имя поставщика для подключения. Это свойство также можно задать по содержимому [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство или *ConnectionString* аргумент [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод; Однако Указание поставщика в нескольких местах во время вызова методов **откройте** метод может иметь непредсказуемые результаты. Если поставщик не указан, свойство по умолчанию MSDASQL ([поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 **Поставщика** свойство доступно чтения и записи, когда подключение будет закрытым или только для чтения, когда он открыт. Параметр не вступили в силу только после откройте **подключения** объекта или доступа [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию **подключения** объекта. Если параметр не является допустимым, возникает ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Provider и Defaultdatabase свойства (Visual Basic)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider и Defaultdatabase свойства (Visual Basic)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Приложение а. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)

---
description: Свойство Provider (ADO)
title: Свойство Provider (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c3f45e8652568bd0440121e27ee6ee0c116e676
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989915"
---
# <a name="provider-property-ado"></a>Свойство Provider (ADO)
Указывает имя поставщика для объекта [соединения](./connection-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, указывающее имя поставщика.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **provider** , чтобы задать или вернуть имя поставщика для соединения. Это свойство также может быть задано содержимым свойства [ConnectionString](./connectionstring-property-ado.md) или аргумента *ConnectionString* метода [Open](./open-method-ado-connection.md) . Однако указание поставщика в нескольких местах при вызове метода **Open** может привести к непредсказуемым результатам. Если поставщик не указан, свойство будет по умолчанию MSDASQL ([поставщик Microsoft OLE DB для ODBC](../../guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 Свойство **provider** доступно для чтения и записи, когда соединение закрывается и доступно только для чтения, когда оно открыто. Параметр вступит в силу только после открытия объекта **соединения** или доступа к коллекции [свойств](./properties-collection-ado.md) объекта **Connection** . Если параметр не является допустимым, возникает ошибка.  
  
## <a name="applies-to"></a>Применение  
 [Объект Connection (ADO)](./connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств provider и DefaultDatabase (Visual Basic)](./provider-and-defaultdatabase-properties-example-vb.md)   
 [Пример свойств provider и DefaultDatabase (Visual Basic)](./provider-and-defaultdatabase-properties-example-vb.md)   
 [Поставщик OLE DB Майкрософт для ODBC](../../guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Приложение А. Поставщики](../../guide/appendixes/appendix-a-providers.md)
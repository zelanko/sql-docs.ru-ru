---
title: StayInSync, свойство | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18d17e0a761fe03053ba90b8ff1ef87f3067df76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67930745"
---
# <a name="stayinsync-property"></a>Свойство StayInSync
Указывает, изменяется ли ссылка на базовые дочерние записи (то есть *глава*) в иерархическом объекте [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) при изменении позиционирования родительской строки.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **логическое** значение. Значение по умолчанию ― **True**. Если **значение равно true**, глава будет обновлена, если родительский объект **Recordset** изменяет расположение строки. Если **значение равно false**, глава продолжит ссылаться на данные в предыдущей главе, несмотря на то, что родительский объект **набора записей** изменил расположение строки.  
  
## <a name="remarks"></a>Remarks  
 Это свойство применяется к иерархическим наборам записей, таким как поддерживаемые [службой формирования данных Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), и должны быть установлены в родительском **наборе записей** до получения дочернего **набора записей** . Это свойство упрощает навигацию по иерархическим наборам записей.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства StayInSync (Visual Basic)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Служба формирования данных Майкрософт для OLE DB (поставщик служб ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

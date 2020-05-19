---
title: Свойство LockType (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
author: rothja
ms.author: jroth
ms.openlocfilehash: 4a8d0f94d4482649030561f2ac71ed6de1374e46
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754487"
---
# <a name="locktype-property-ado"></a>Свойство LockType (ADO)
Указывает тип блокировок, помещаемых в записи во время редактирования.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [локктипинум](../../../ado/reference/ado-api/locktypeenum.md) . Значение по умолчанию — **адлоккреадонли**.  
  
## <a name="remarks"></a>Remarks  
 Задайте свойство **LockType** перед открытием [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , чтобы указать, какой тип блокировки должен использоваться поставщиком при его открытии. Прочтите свойство, чтобы получить тип блокировки, используемой для открытого объекта **набора записей** .  
  
 Поставщики могут не поддерживать все типы блокировок. Если поставщик не поддерживает запрошенный параметр **LockType** , он заменит другой тип блокировки. Чтобы определить фактические функциональные возможности блокировки, доступные в объекте **Recordset** , используйте метод [поддерживает](../../../ado/reference/ado-api/supports-method.md) с **адупдате** и **адупдатебатч**.  
  
 Параметр **адлоккпессимистик** не поддерживается, если свойство [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) имеет значение **адусеклиент**. Если задано неподдерживаемое значение, то ошибка не будет возникать. Вместо этого будет использоваться ближайший поддерживаемый **LockType** .  
  
 Свойство **LockType** доступно для чтения и записи, когда **набор записей** закрывается и только для чтения, когда он открыт.  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании объекта **набора записей** на стороне клиента свойство **LockType** может иметь только значение **адлоккбатчоптимистик**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств примеры CursorType, LockType и EditMode (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Пример свойств примеры CursorType, LockType и EditMode (Visual c++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)

---
title: Свойство Bookmark (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 48b1c90b59b220841aa45f618fdfda5ff2db82da
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920341"
---
# <a name="bookmark-property-ado"></a>Свойство Bookmark (ADO)
Указывает закладку, которая уникально идентифицирует текущую запись в объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) или устанавливает текущую запись в объекте **набора записей** в запись, определяемую допустимой закладкой.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает выражение **типа Variant** , результатом которого является допустимая закладка.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Bookmark** используется для сохранения позиции текущей записи и возврата к этой записи в любое время. Закладки доступны только в объектах **набора записей** , поддерживающих функциональность закладок.  
  
 При открытии объекта **набора записей** каждая из его записей имеет уникальную закладку. Чтобы сохранить закладку для текущей записи, присвойте переменной значение свойства **Bookmark** . Чтобы быстро вернуться к этой записи в любое время после перехода на другую запись, задайте для свойства **Bookmark** объекта **Recordset** значение этой переменной.  
  
 Возможно, пользователь не сможет просмотреть значение закладки. Кроме того, пользователи не должны предполагать, что закладки напрямую сравнимы, так как две закладки, которые ссылаются на одну и ту же запись, могут иметь разные значения.  
  
 Если для создания копии объекта **набора записей** используется метод [clone](../../../ado/reference/ado-api/clone-method-ado.md) , то параметры свойств **закладки** для исходного и повторяющегося объектов **набора записей** идентичны, и их можно использовать взаимозаменяемыми. Однако нельзя использовать закладки из разных объектов **набора записей** , даже если они были созданы из одного и того же источника или команды.  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании объекта **набора записей** на стороне клиента свойство **Bookmark** всегда доступно.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств BOF, EOF и Bookmark (Visual Basic)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [Пример свойств BOF, EOF и Bookmark (Visual c++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)

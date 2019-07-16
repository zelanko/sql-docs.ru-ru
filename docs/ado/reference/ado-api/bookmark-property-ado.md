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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920341"
---
# <a name="bookmark-property-ado"></a>Свойство Bookmark (ADO)
Указывает закладка, которая однозначно определяет текущую запись в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта или задает текущую запись **записей** объект для записи, определяемой закладкой допустимым.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Variant** выражение, результатом которого является допустимый закладка.  
  
## <a name="remarks"></a>Примечания  
 Используйте **закладки** свойство, чтобы сохранить позицию текущей записи и в любое время вернуться к этой записи. Закладки доступны только в **записей** объектов, которые поддерживают функцию закладок.  
  
 При открытии **записей** объекта, каждый из него записей с закладкой уникальным. Чтобы сохранить закладку в текущей записи, назначьте **закладки** свойства переменной. Чтобы быстро вернуться к этой записи в любое время после перехода на другую запись, задайте **записей** объекта **закладки** в соответствии с значением этой переменной.  
  
 Пользователь не может иметь возможность просматривать значение закладки. Кроме того пользователям не следует ожидать закладки, чтобы быть сопоставимыми напрямую, так как два закладки, которые ссылаются на той же записи могут иметь разные значения.  
  
 При использовании [клона](../../../ado/reference/ado-api/clone-method-ado.md) метод, чтобы создать копию **записей** объекта, **закладки** параметры свойств для исходной и дубликат **набора записей**  объекта идентичны объектам, и их можно использовать как взаимозаменяемые. Тем не менее, нельзя использовать закладки из разных **записей** объекты являются взаимозаменяемыми, даже если они были созданы из одного источника или команды.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объекта, **закладки** свойство всегда доступно.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [BOF, EOF и Bookmark Example свойства (Visual Basic)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF, EOF и Bookmark Example свойства (Visual C++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)

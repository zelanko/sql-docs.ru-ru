---
title: Bookmark-свойство (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e645300f604e1880f98fd8d99cea8599062f72f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276203"
---
# <a name="bookmark-property-ado"></a>Свойство закладка (ADO)
Указывает закладка, которая однозначно определяет текущую запись в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта или задает текущую запись **записей** объект для записи, определяемый допустимую закладку.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Variant** выражение, результатом которого является допустимое закладка.  
  
## <a name="remarks"></a>Примечания  
 Используйте **закладки** свойство, чтобы сохранить позицию текущей записи и вернуться на эту запись в любое время. Закладки, доступны только в **записей** объектов, которые поддерживают функцию закладок.  
  
 При открытии **записей** объектов, каждый из него записей имеет уникальный закладки. Чтобы сохранить закладку в текущей записи, присвойте значение **закладки** свойства переменной. Чтобы быстро вернуться к этой записи в любое время после перемещения в другой записи, задайте **записей** объекта **закладки** значение этой переменной.  
  
 Пользователь может не иметь возможность просматривать значения закладки. Кроме того пользователи не должен ожидать закладки, чтобы быть сравнить непосредственно, так как две закладки, ссылающиеся на ту же запись может иметь разные значения.  
  
 При использовании [клон](../../../ado/reference/ado-api/clone-method-ado.md) метод для создания копии **записей** объекта, **закладки** значений свойств исходного и дубликат **набора записей**  объекты идентичны, и их можно использовать попеременно. Тем не менее, нельзя использовать закладки из разных **записей** объектов взаимозаменяемо, даже если они были созданы из одного источника или команды.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объекта, **закладки** свойство доступна всегда.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [BOF EOF и пример свойства закладки (Visual Basic)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF EOF и пример свойства закладки (VC ++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)

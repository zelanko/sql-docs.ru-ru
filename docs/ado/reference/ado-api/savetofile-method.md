---
title: Метод SaveToFile | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6afe36c7b3923c9ebf33fd615a1c21e34955e62d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63315221"
---
# <a name="savetofile-method"></a>Метод SaveToFile
Сохраняет содержимое двоичных [Stream](../../../ado/reference/ado-api/stream-object-ado.md) в файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Параметры  
 *FileName*  
 Объект **строка** значение, содержащее полное имя файла, к которому содержимое **Stream** будут сохранены. Можно сохранить любое действительное расположение на локальном или любое расположение у вас есть доступ к по значение UNC.  
  
 *Объект SaveOptions*  
 Объект [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md) значение, указывающее, должен ли быть создан новый файл с **SaveToFile**, если он еще не существует. Значение по умолчанию — **adSaveCreateNotExists**. С этими параметрами можно указать, что, если указанный файл не существует, возникает ошибка. Можно также указать, что **SaveToFile** перезаписывает текущее содержимое существующего файла.  
  
> [!NOTE]
>  Если перезаписать существующий файл (при **adSaveCreateOverwrite** имеет значение), **SaveToFile** усекает все байты из существующего исходного файла, выполните новый [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Примечания  
 **SaveToFile** может использоваться для копирования содержимого **Stream** объекта в локальный файл. Нет изменений в содержимое или свойства **Stream** объекта. **Stream** объект должен быть открыт до вызова метода **SaveToFile**.  
  
 Этот метод не изменяет связь **Stream** объекта его базовый источник. **Stream** объект по-прежнему будет связан с исходный URL-адрес или **записи** , который был источником при открытии.  
  
 После **SaveToFile** операция, текущей позиции ([позиции](../../../ado/reference/ado-api/position-property-ado.md)) в потоке имеет значение начала потока (0).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Open (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)

---
title: Метод SaveToFile | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9beb8a1e2bfcc307c93b293a35dcac26cf0847a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="savetofile-method"></a>Метод SaveToFile
Сохраняет двоичное содержимое [поток](../../../ado/reference/ado-api/stream-object-ado.md) в файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Параметры  
 *FileName*  
 Объект **строка** значение, содержащее полное имя файла, на которую содержимое **поток** будут сохранены. Можно сохранить любое допустимое локальное расположение или любое место доступны через значение UNC.  
  
 *Объект SaveOptions*  
 Объект [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md) значение, указывающее, следует ли создавать новый файл с **SaveToFile**, если он еще не существует. Значение по умолчанию — **adSaveCreateNotExists**. С помощью этих параметров можно указать, что, если указанный файл не существует, возникает ошибка. Можно также указать, что **SaveToFile** перезаписывает содержимое текущей существующего файла.  
  
> [!NOTE]
>  Если перезаписать существующий файл (если **adSaveCreateOverwrite** имеет значение), **SaveToFile** усекает все байты из существующего исходного файла, выполните новый [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Замечания  
 **SaveToFile** может использоваться для копирования содержимого **поток** объекта в локальный файл. Нет изменений в содержимое или свойства **поток** объекта. **Поток** объект должен быть открыт перед вызовом метода **SaveToFile**.  
  
 Этот метод не изменяет связь **поток** объекта его источнику. **Поток** объект по-прежнему будут связаны с исходный URL-адрес или **записи** был при открытии источника.  
  
 После **SaveToFile** операции, текущая позиция ([позиции](../../../ado/reference/ado-api/position-property-ado.md)) в потоке равно начала потока (0).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)

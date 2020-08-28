---
description: Метод SaveToFile
title: Метод SaveToFile | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6aa3269e73f9823eb47dddeb039b62e3affdd3c6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989295"
---
# <a name="savetofile-method"></a>Метод SaveToFile
Сохраняет двоичное содержимое [потока](./stream-object-ado.md) в файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Параметры  
 *FileName*  
 **Строковое** значение, содержащее полное имя файла, в который будет сохранено содержимое **потока** . Можно сохранить в любое допустимое локальное расположение или любое доступное расположение через UNC-значение.  
  
 *SaveOptions*  
 Значение [савеоптионсенум](./saveoptionsenum.md) , указывающее, должен ли новый файл создаваться с помощью **SaveToFile**, если он еще не существует. Значение по умолчанию — **адсавекреатенотексистс**. С помощью этих параметров можно указать, что ошибка возникает, если указанный файл не существует. Можно также указать, что **SaveToFile** перезаписывает текущее содержимое существующего файла.  
  
> [!NOTE]
>  Если перезаписать существующий файл (когда **адсавекреатеоверврите** установлен), **SaveToFile** усекает все байты из исходного существующего файла, который соответствует новому [EOS](./eos-property.md).  
  
## <a name="remarks"></a>Remarks  
 **SaveToFile** может использоваться для копирования содержимого объекта **потока** в локальный файл. Содержимое или свойства объекта **Stream** не изменяются. Перед вызовом **SaveToFile**объект **потока** должен быть открытым.  
  
 Этот метод не изменяет связь объекта **потока** с базовым источником. Объект **потока** по-прежнему будет связан с исходным URL-адресом или **записью** , которая была источником при открытии.  
  
 После операции **SaveToFile** текущая координата ([положением](./position-property-ado.md)) в потоке устанавливается в начало потока (0).  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Open (поток ADO)](./open-method-ado-stream.md)   
 [Метод Save](./save-method.md)
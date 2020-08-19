---
description: Свойство Mode (ADO)
title: Свойство Mode (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Mode
- _Stream::Mode
- _Record::Mode
helpviewer_keywords:
- Mode property [ADO]
ms.assetid: 808661eb-0d7c-4e6d-8e40-9dc3bef3d77a
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fd002f54010a9bc8d5cf543fe1fd4521bc6d221
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443256"
---
# <a name="mode-property-ado"></a>Свойство Mode (ADO)
Указывает доступные разрешения для изменения данных в [соединении](../../../ado/reference/ado-api/connection-object-ado.md), [записи](../../../ado/reference/ado-api/record-object-ado.md)или объекте [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [коннектмодинум](../../../ado/reference/ado-api/connectmodeenum.md) . Значение по умолчанию для **соединения** — **адмодеункновн**. Значение по умолчанию для объекта **Record** — **адмодереад**. Значение по умолчанию для **потока** , связанного с базовым источником (открытым с URL-адресом в качестве источника или в качестве **потока** по умолчанию **записи**), — **адмодереад**. Значение по умолчанию для **потока** , не связанного с базовым источником (экземпляром в памяти), — **адмодеункновн**.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **mode** , чтобы задать или вернуть разрешения на доступ, используемые поставщиком в текущем соединении. Свойство **mode** можно задать только в том случае, если объект **соединения** закрыт.  
  
 Для объекта **потока** , если режим доступа не указан, он наследуется из источника, используемого для открытия объекта **потока** . Например, если **поток** открыт из объекта **Record** , по умолчанию он открывается в том же режиме, что и **запись**.  
  
 Это свойство доступно для чтения и записи, пока объект закрыт и доступен только для чтения, пока открыт объект.  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании объекта **подключения** на стороне клиента для свойства **mode** можно задать только значение **адмодеункновн**.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Пример свойств IsolationLevel и Mode (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [Пример свойств IsolationLevel и Mode (Visual c++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   

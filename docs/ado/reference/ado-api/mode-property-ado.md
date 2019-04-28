---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fc2a9dffe5dc22c1dadfa075b91d8a6b26215de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863681"
---
# <a name="mode-property-ado"></a>Свойство Mode (ADO)
Указывает доступные разрешения для изменения данных в [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [записи](../../../ado/reference/ado-api/record-object-ado.md), или [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) значение. Значение по умолчанию для **подключения** — **adModeUnknown**. Значение по умолчанию для **записи** объект **adModeRead**. Значение по умолчанию для **Stream** связанные с базового источника (открыть URL-адрес, как источник или как значение по умолчанию **Stream** из **записи**) является  **adModeRead**. Значение по умолчанию для **Stream** не связана с основной источник (экземпляр в памяти) — **adModeUnknown**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **режим** свойство задание или возврат права доступа используется поставщиком для текущего соединения. Можно задать **режим** свойства только тогда, когда **подключения** объект закрыт.  
  
 Для **Stream** объекта, если режим доступа не указано, оно наследуется из источника, используемый для открытия **Stream** объекта. Например если **Stream** открывается из **записи** объекта по умолчанию, то он открывается в один и тот же режим как **записи**.  
  
 Это свойство является чтение и запись, пока объект является закрытым или только для чтения, пока открыт объект.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **режим** свойство может устанавливаться только **adModeUnknown**.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Примеры IsolationLevel и Mode свойства (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [Примеры IsolationLevel и Mode свойства (Visual C++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   

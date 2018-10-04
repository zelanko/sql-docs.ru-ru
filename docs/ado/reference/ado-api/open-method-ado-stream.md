---
title: Метод (ADO Stream) Open | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Open
- _Stream::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: d26f48fb-904e-4932-a245-3b4332ca1600
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0df165514a10bc667c8bd2cc6d2a8569faa79d11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611422"
---
# <a name="open-method-ado-stream"></a>Метод Open (объект Stream ADO)
Открывает [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта для обработки потоков данных двоичное или текстовое.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный параметр. Объект **Variant** значение, указывающее источник данных для **Stream**. *Источник* может содержать строку абсолютный URL-адрес, который указывает на существующий узел в хорошо известных древовидной структуры, например системы электронной почты или файл. URL-адрес должен быть указан с помощью ключевого слова URL-адрес ("URL-адрес =*схемы*://*server*/*папку*«). Кроме того *источника* может содержать ссылку на уже открытого [записи](../../../ado/reference/ado-api/record-object-ado.md) объект, который открывает поток по умолчанию, связанные с **записи**. Если *источника* не указан, **Stream** создан и открыт, связанные с без базового источника по умолчанию. Дополнительные сведения о схемы URL-адресов и соответствующих поставщиков, см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 *Режим*  
 Необязательный параметр. Объект [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) значение, указывающее режим доступа для результирующего **Stream** (например, чтение и запись или только для чтения). Значение по умолчанию — **adModeUnknown**. См. в разделе [режим](../../../ado/reference/ado-api/mode-property-ado.md) Дополнительные сведения о режимах доступа. Если *режим* не указан, он наследуется исходного объекта. Например если источник **записи** открыт в режиме только для чтения, **Stream** также открывается в режиме только для чтения по умолчанию.  
  
 *OpenOptions*  
 Необязательный параметр. Объект [StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md) значение. Значение по умолчанию — **adOpenStreamUnspecified**.  
  
 *UserName*  
 Необязательный параметр. Объект **строка** значение, содержащее идентификатор пользователя, который, при необходимости, обращается к **Stream** объекта.  
  
 *Пароль*  
 Необязательный параметр. Объект **строка** значение, содержащее пароль, который при необходимости, обращается к **Stream** объекта.  
  
## <a name="remarks"></a>Примечания  
 Когда **записи** объект передается как параметр источника *UserID* и *пароль* параметры не используются, так как доступ к **записи** объект уже доступен. Аналогичным образом [режим](../../../ado/reference/ado-api/mode-property-ado.md) из **записи** передается объект **Stream** объекта. Когда *источника* не указан, **Stream** открыт не содержит данных и имеет [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) нуль (0). Чтобы избежать потери данных, которые записаны в **Stream** при **Stream** будет закрыто, Сохранить **Stream** с [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) или [ SaveToFile](../../../ado/reference/ado-api/savetofile-method.md) методов, или сохранить его в другом месте памяти.  
  
 *OpenOptions* значение **adOpenStreamFromRecord** определяет содержание *источника* параметр будет уже открытого **записи**объекта. Поведение по умолчанию — обрабатывать *источника* как URL-адрес, указывающий непосредственно к узлу в виде древовидной структуры, например файл. Открытие потока по умолчанию, связанные с этим узлом.  
  
 Хотя **Stream** является не открыто, можно прочитать все свойства только для чтения для **Stream**. Если **Stream** открыт асинхронно, все последующие операции (отличное от проверки [состояние](../../../ado/reference/ado-api/state-property-ado.md) и другие свойства только для чтения) будут заблокированы, пока **откройте** Операция завершена.  
  
 Помимо параметров, которые были описаны ранее, не указывая *источника*, можно создать экземпляр **Stream** объект в памяти, не связывая его с базового источника. Можно динамически добавлять данные в поток, записывая двоичные или текстовые данные для **Stream** с [записи](../../../ado/reference/ado-api/write-method.md) или [WriteText](../../../ado/reference/ado-api/writetext-method.md), или, загружая данные из файла с [ LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)   
 [Метод SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)

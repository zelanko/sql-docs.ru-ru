---
title: Open-метод (поток ADO) | Документы Microsoft
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
- _Stream::raw_Open
- _Stream::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: d26f48fb-904e-4932-a245-3b4332ca1600
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44493854720564e241817c1b482339f9c5cbbd32
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="open-method-ado-stream"></a>Метод Open (поток ADO)
Открывает [поток](../../../ado/reference/ado-api/stream-object-ado.md) для работы потоков двоичных или текстовых данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательно. Объект **Variant** значение, указывающее источник данных для **поток**. *Источник* может содержать строку абсолютный URL-адрес, указывающий на существующий узел в хорошо известных древовидная структура, например по электронной почте или файловая система. URL-адрес указывается с помощью ключевого слова URL-адрес ("URL-адрес =*схема*://*сервера*/*папки*»). Кроме того *источника* может содержать ссылку на уже открытого [запись](../../../ado/reference/ado-api/record-object-ado.md) объекта, который открывает поток по умолчанию, связанные с **записи**. Если *источника* не указан, **поток** создан и открыт, связанные без базового источника по умолчанию. Дополнительные сведения о URL-схем и соответствующих поставщиков см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 *Режим*  
 Необязательно. Объект [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) значение, указывающее режим доступа для результирующего **поток** (например, чтение и запись или только для чтения). Значение по умолчанию — **adModeUnknown**. В разделе [режим](../../../ado/reference/ado-api/mode-property-ado.md) Дополнительные сведения о режимах доступа. Если *режим* не указано, оно наследуется из объекта источника. Например если источник **запись** открывается в режиме только для чтения, **поток** также открывается в режиме только для чтения по умолчанию.  
  
 *OpenOptions*  
 Необязательно. Объект [StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md) значение. Значение по умолчанию — **adOpenStreamUnspecified**.  
  
 *UserName*  
 Необязательно. Объект **строка** значение, содержащее идентификатор пользователя, при необходимости, обращается к **поток** объекта.  
  
 *Пароль*  
 Необязательно. Объект **строка** значение, содержащее пароль, при необходимости, обращается к **поток** объекта.  
  
## <a name="remarks"></a>Замечания  
 Когда **запись** объект передается как параметр источника *UserID* и *пароль* параметры не используются, так как доступ к **записи** объекта уже доступна. Аналогичным образом [режим](../../../ado/reference/ado-api/mode-property-ado.md) из **запись** передается объект **поток** объекта. Когда *источника* не указан, **поток** открыть не содержит данных и имеет [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) нуль (0). Во избежание потери данных, записываемых это **поток** при **поток** — закрыто, Сохранить **поток** с [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) или [ SaveToFile](../../../ado/reference/ado-api/savetofile-method.md) методов, или сохранить его в другое расположение в памяти.  
  
 *OpenOptions* значение **adOpenStreamFromRecord** определяет содержимое *источника* параметр должен быть уже открытого **запись**объекта. Поведение по умолчанию — обрабатывать *источника* как URL-адрес, указывающий на узел в древовидной структуре, например файл. Открытие потока по умолчанию, связанные с этим узлом.  
  
 Хотя **поток** — не открыто, можно прочитать все свойства только для чтения для **поток**. Если **поток** открыт асинхронно, все последующие операции (отличный от проверки [состояние](../../../ado/reference/ado-api/state-property-ado.md) и другие свойства только для чтения), блокируются до **откройте** Операция завершена.  
  
 Помимо параметров, которые были описаны ранее, не указывая *источника*, можно создать экземпляр **поток** объект в памяти, не связывая его с базового источника. Можно динамически добавлять данные в поток, написав двоичные или текстовые данные **поток** с [записи](../../../ado/reference/ado-api/write-method.md) или [WriteText](../../../ado/reference/ado-api/writetext-method.md), или путем загрузки данных из файла с [ LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Open (соединение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (ADO запись)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)   
 [Метод SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)

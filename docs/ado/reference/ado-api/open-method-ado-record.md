---
title: Метод (объект Record ADO) Open | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97c7f1c143c83dd35ca5ff17e9776d79fb734ff9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917926"
---
# <a name="open-method-ado-record"></a>Метод Open (объект Record ADO)
Открывает существующий [записи](../../../ado/reference/ado-api/record-object-ado.md) объект или создает новый элемент, представленный **записи**, например файла или каталога.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный параметр. Объект **Variant** , может представлять URL-адрес сущности, представляемый этим **записи** объекта, **команда**, открытую [записей](../../../ado/reference/ado-api/recordset-object-ado.md) или другой **записи** объект, строка, содержащая инструкцию SQL SELECT или имя таблицы.  
  
 *ActiveConnection*  
 Необязательный. Объект **Variant** , представляющее строку подключения или открыть [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
 *Режим*  
 Необязательный. Объект [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) значение, указывающее режим доступа для результирующего **записи** объекта. Значение по умолчанию — **adModeUnknown**.  
  
 *CreateOptions*  
 Необязательный параметр. Объект [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) значение, указывающее, следует открыть существующий файл или каталог, или должен будет создан новый файл или каталог. Значение по умолчанию — **adFailIfNotExists**. Если присвоено значение по умолчанию, режим доступа получается из [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство. Этот параметр учитывается при *источника* параметр не содержит URL-адрес.  
  
 *Параметры*  
 Необязательный параметр. Объект [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md) значение, указывающее параметры для открытия **записи**. Значение по умолчанию — **adOpenRecordUnspecified**. Эти значения можно объединять.  
  
 *UserName*  
 Необязательный параметр. Объект **строка** значение, содержащее идентификатор пользователя, если это необходимо, разрешает доступ к *источника*.  
  
 *Пароль*  
 Необязательный параметр. Объект **строка** значение, содержащее пароль, который при необходимости, проверяет ли *UserName*.  
  
## <a name="remarks"></a>Примечания  
 *Источник* может быть:  
  
-   URL-АДРЕС. Если используется протокол для URL-адрес http, поставщик Интернета будет вызываться по умолчанию. Если URL-адрес будет указывать на узел, содержащий исполняемый сценарий (такие как. ASP-странице), **записи** , содержащий источник вместо выполненной содержимое открыт по умолчанию. Используйте *параметры* аргумент, чтобы изменить это поведение.  
  
-   Объект **записи** объекта. Объект **записи** открыть объект из другого **записи** будет клонировать исходный **записи** объекта.  
  
-   Объект **команда** объекта. Открытый **записи** представляет одну строку, возвращаемым при выполнении инструкции **команда**. Если результаты содержат более одной строки, содержимое первой строки помещаются в запись, и ошибка может быть добавлена к **ошибки** коллекции.  
  
-   Инструкцию SQL SELECT. Открытый **запись** представляет одну строку, возвращаемым при выполнении инструкции содержимое строки. Если результаты содержат более одной строки, содержимое первой строки помещаются в запись, и ошибка может быть добавлена к **ошибки** коллекции.  
  
-   Имя таблицы.  
  
 Если **записи** представляет сущность, которая будет недоступно с URL-адрес (например, строку **записей** производным от базы данных), значения [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)свойства и поля, для доступа к **adRecordURL** константы имеют значение null.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)

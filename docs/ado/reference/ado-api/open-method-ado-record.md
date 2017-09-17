---
title: "Open-метод (запись ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7e7f1c5e35ced700818954056b380a44c75570c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="open-method-ado-record"></a>Метод Open (ADO запись)
Открывает существующий [запись](../../../ado/reference/ado-api/record-object-ado.md) объект или создает новый элемент, представленный **записи**, таких как файл или каталог.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательно. Объект **Variant** , может представлять URL-адрес сущности, представляемый этим экземпляром **записи** объекта, **команда**, открытый [записей](../../../ado/reference/ado-api/recordset-object-ado.md) или другой **записи** объект, строка, содержащая инструкцию SQL SELECT или имя таблицы.  
  
 *ActiveConnection*  
 Необязательно. Объект **Variant** , представляющее строку подключения или открыть [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
 *Режим*  
 Необязательно. Объект [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) значение, указывающее режим доступа для результирующего **записи** объекта. Значение по умолчанию — **adModeUnknown**.  
  
 *CreateOptions*  
 Необязательно. Объект [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) значение, указывающее, следует открыть существующий файл или каталог, или необходимо создать новый файл или каталог. Значение по умолчанию — **adFailIfNotExists**. Если задано значение по умолчанию, режим доступа будет получен из [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство. Этот параметр учитывается при *источника* параметр не содержит URL-адрес.  
  
 *Параметры*  
 Необязательно. Объект [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md) значение, указывающее параметры для открытия **записи**. Значение по умолчанию — **adOpenRecordUnspecified**. Эти значения могут быть объединены.  
  
 *UserName*  
 Необязательно. Объект **строка** значение, содержащее идентификатор пользователя, если это необходимо, дающая право на доступ к *источника*.  
  
 *Пароль*  
 Необязательно. Объект **строка** значение, содержащее пароль, если это требуется, проверяет *UserName*.  
  
## <a name="remarks"></a>Замечания  
 *Источник* может быть:  
  
-   URL-АДРЕС. Если протокол для URL-адрес http, будет вызван поставщика Интернета по умолчанию. Если URL-адрес указывает на узел, содержащий исполняемый скрипт (такие как. ASP-странице), **записи** , содержащий источник вместо выполненной открытии содержимое по умолчанию. Используйте *параметры* аргумент, чтобы изменить это поведение.  
  
-   Объект **записи** объекта. Объект **запись** открыть объект от другого **записи** будет клонирования исходный **записи** объекта.  
  
-   Объект **команда** объекта. Открытый **запись** представляет одну строку, возвращенными в результате выполнения **команда**. Если результаты содержат больше одной строки, содержимое первой строки помещаются в записи и ошибки могут быть добавлены к **ошибки** коллекции.  
  
-   Инструкцию SQL SELECT. Открытый **запись** представляет одну строку, возвращенными в результате выполнения содержимое строки. Если результаты содержат больше одной строки, содержимое первой строки помещаются в записи и ошибки могут быть добавлены к **ошибки** коллекции.  
  
-   Имя таблицы.  
  
 Если **запись** объект представляет собой сущность, к которому невозможно получить URL-адрес (например, строку **записей** производным от базы данных), оба значения [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)свойства и поля, доступ к **adRecordURL** константы имеют значение null.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод Open (соединение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)

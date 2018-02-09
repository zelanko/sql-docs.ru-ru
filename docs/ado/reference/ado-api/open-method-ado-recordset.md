---
title: "Open-метод (набора записей ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::raw_Open
- Recordset15::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 74e6fc58d5b32313806301467ca48b9f033b083b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="open-method-ado-recordset"></a>Метод Open (набора записей ADO)
Открывает курсор на [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательно. Объект **Variant** , результат вычисления которого является допустимым [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, инструкции SQL, имя таблицы, вызов хранимой процедуры, URL-адрес или имя файла или [поток](../../../ado/reference/ado-api/stream-object-ado.md) объект, содержащий постоянно хранить [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 *ActiveConnection*  
 Необязательно. Либо **Variant** , результат вычисления которого является допустимым [подключения](../../../ado/reference/ado-api/connection-object-ado.md) переменная с именем объекта или **строка** , содержащий [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) параметры.  
  
 *CursorType*  
 Необязательно. Объект [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) значение, определяющее тип курсора, поставщик следует использовать при открытии **записей**. Значение по умолчанию — **adOpenForwardOnly**.  
  
 *LockType*  
 Необязательно. Объект [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) значение, которое определяет, какой тип блокировки (параллелизма) поставщик следует использовать при открытии **записей**. Значение по умолчанию — **adLockReadOnly**.  
  
 *Параметры*  
 Необязательно. A **Long** значение, указывающее, как следует оценивать поставщик *источника* аргумент, если что-то отличное от **команда** объекта, или что **Записей** должен быть восстановлен из файла, в котором он был ранее сохранен. Может быть один или несколько [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) или [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения, которые могут быть объединены с помощью побитового оператора OR.  
  
> [!NOTE]
>  При открытии **записей** из **поток** содержащий материализованный **записей**, с использованием [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значение **adAsyncFetchNonBlocking** не будет действовать, fetch синхронный и блокировки.  
  
> [!NOTE]
>  **ExecuteOpenEnum** значения **adExecuteNoRecords** или **adExecuteStream** не должны использоваться с **откройте**.  
  
## <a name="remarks"></a>Remarks  
 Курсор по умолчанию для ADO **записей** курсора однопроходный, только для чтения, расположенные на сервере.  
  
 С помощью **откройте** метод **записей** объект, он открывается курсор, который представляет записей из базовой таблицы, результаты запроса или ранее сохраненного **набора записей**.  
  
 Использовать необязательный *источника* аргумент, чтобы указать источник данных, с помощью одного из следующих действий: **команда** объектную переменную, инструкции SQL, хранимая процедура, имя таблицы, URL-адрес или полное имя пути. Если *источника* является именем пути файла можно указать полный путь («c:\dir\file.rst»), относительный путь («.. \file.RST»), или URL-адрес («http://files/file.rst»).  
  
 Не рекомендуется использовать *источника* аргумент **откройте** метод, чтобы выполнить запрос на изменение, не возвращает записи, так как нет простого способа определить, успешно ли выполнен вызов. **Записей** возвращенных таких запрос будет закрыт. Чтобы выполнить запрос, который не возвращает записи, например инструкцию SQL INSERT, вызовите [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод **команда** объекта или [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод [Подключения](../../../ado/reference/ado-api/connection-object-ado.md) вместо этого объекта.  
  
 *ActiveConnection* аргумент соответствует [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойства и указывает, какое подключение, чтобы открыть **записей** объекта. Если передать определение подключения для этого аргумента ADO открывает новое соединение, используя указанные параметры. После открытия **записей** с клиентский курсор, задав [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**, можно изменить значение этого свойства для отправки обновления для другого поставщика. Или можно присвоить этому свойству **ничего** (в Microsoft Visual Basic) или значение NULL, чтобы отключить **записей** из любого поставщика. Изменение *ActiveConnection* для серверный курсор, однако приведет к ошибке.  
  
 Для аргументов, которые соответствуют свойствам **записей** объекта (*источника*, *CursorType*, и *LockType*), связь аргументов в свойствах выглядит следующим образом:  
  
-   Чтение и запись, прежде чем оно **записей** открыть объект.  
  
-   Параметры используются только при проведении соответствующих аргументов при выполнении **откройте** метод. При передаче аргумента, оно переопределяет значение соответствующего свойства и значение свойства обновляется значение аргумента.  
  
-   После открытия **записей** объекта, эти свойства доступны только для чтения.  
  
> [!NOTE]
>  **ActiveConnection** свойство доступно только для чтения для **записей** объектов, [источника](../../../ado/reference/ado-api/source-property-ado-recordset.md) задано допустимое **команда** объекта, даже если **записей** объектов не открыт.  
  
 При передаче **команда** объекта в *источника* аргумент, а также проход *ActiveConnection* аргументов, возникает ошибка. **ActiveConnection** свойство **команда** объект должен уже быть задано допустимое **подключения** объект или строка соединения.  
  
 Если что-то отличное от передать **команда** объекта в *источника* аргумент, можно использовать *параметры* аргумент для оптимизации вычисление *источника*  аргумент. Если *параметры* аргумент не задан, могут возникнуть снижение производительности, так как ADO необходимо выполнять вызовы к поставщику, чтобы определить, является ли аргумент инструкции SQL, хранимая процедура, URL-адрес или имя таблицы. Если вы знаете, что *источника* использовании, параметр типа *параметры* аргумент указывает, что ADO, чтобы перейти на соответствующий код. Если *параметры* аргумент не соответствует *источника* типа, возникает ошибка.  
  
 Если передать **поток** объекта в *источника* аргумент, не следует передавать сведения в других аргументов. Это приведет к ошибке. **ActiveConnection** информация не сохраняется при **записей** открывается из **поток**.  
  
 Значение по умолчанию для *параметры* аргумент **adCmdFile** Если нет соединения, связанные с **записей**. Обычно это будет регистр для постоянно хранить **записей** объектов.  
  
 Если источник данных не возвращает записи, то поставщик устанавливает оба [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) и [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойства **True**, и положение текущей записи не определено. По-прежнему можно добавлять новые данные в этом пустой **записей** объекта, если тип курсора позволяет ей.  
  
 После завершения операции через открытый **записей** , используйте [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод, чтобы освободить все связанные с ним ресурсы системы. Закрывает объект не удаляется из памяти; можно изменить настройки его свойств и использовать **откройте** метод, чтобы открыть его позже. Для полного устранения объекта из памяти, присвойте переменной объекта *ничего не*.  
  
 Перед **ActiveConnection** свойство задано, вызовите метод **откройте** с не операндами, для создания экземпляра **записей** создан путем добавления поля к  **Набор записей** [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции.  
  
 Если вы задали [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**, можно получить асинхронно в одном из двух способов. Рекомендуется установить *параметры* для **adAsyncFetch**. Кроме того, можно использовать «Asynchronous Processing строк» динамических свойств в [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции, но связанные события, полученные могут быть потеряны, если не задано *параметры* параметра **adAsyncFetch**.  
  
> [!NOTE]
>  Выборка фоновой мс удаленного поставщика поддерживается только с использованием **откройте** метода *параметры* параметра.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Определенные сочетания [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) и [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения недопустимы. Сведения о том, какие параметры нельзя использовать вместе, см. в разделах для [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md), и [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Открытие и закрытие примере методы (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Пример методов открытия и закрытия (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Пример методов открытия и закрытия (VC ++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Сохранение и открытие примере методы (Visual Basic)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Метод Open (соединение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (ADO запись)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)

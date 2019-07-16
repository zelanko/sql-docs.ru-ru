---
title: Метод (объект Recordset ADO) Open | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Open
- Recordset15::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 16142f200e6fd6e7c141b4f1fe6d45fe8917bc28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931902"
---
# <a name="open-method-ado-recordset"></a>Метод Open (объект Recordset ADO)
Открывает курсор на [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный. Объект **Variant** , результатом которого является допустимым является [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, инструкции SQL, имя таблицы, вызов хранимой процедуры, URL-адрес или имя файла или [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объект, содержащий постоянно храниться [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 *ActiveConnection*  
 Необязательный параметр. Либо **Variant** , результатом которого является допустимым является [подключения](../../../ado/reference/ado-api/connection-object-ado.md) переменная с именем объекта или **строка** , содержащий [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) параметры.  
  
 *Примеры CursorType*  
 Необязательный. Объект [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) значение, определяющее тип курсора, поставщик следует использовать при открытии **записей**. Значение по умолчанию — **adOpenForwardOnly**.  
  
 *LockType*  
 Необязательный параметр. Объект [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) значение, которое определяет, какой тип блокировки (параллелизм) поставщик следует использовать при открытии **записей**. Значение по умолчанию — **adLockReadOnly**.  
  
 *Параметры*  
 Необязательный параметр. Объект **Long** значение, указывающее, каким образом следует оценить, поставщик *источника* аргумент, если что-то отличное от **команда** объекта или, **Записей** должен быть восстановлен из файла, где он был ранее сохранен. Может быть один или несколько [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) или [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения, которые могут быть объединены с помощью побитового оператора OR.  
  
> [!NOTE]
>  При открытии **записей** из **Stream** содержащий материализованный **записей**, с использованием [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значение **adAsyncFetchNonBlocking** не окажет никакого воздействия; выборка будет иметь синхронной и блокировки.  
  
> [!NOTE]
>  **ExecuteOpenEnum** значения **adExecuteNoRecords** или **adExecuteStream** не должны использоваться с **откройте**.  
  
## <a name="remarks"></a>Примечания  
 Курсор по умолчанию для ADO **записей** курсор однопроходный, только для чтения, расположенных на сервере.  
  
 С помощью **откройте** метод **записей** открывается курсор, который представляет записей из базовой таблицы, результаты запроса, или ранее сохраненному **записей**.  
  
 Используйте необязательный *источника* аргумент, чтобы указать источник данных, с помощью одного из следующих: **команда** объектной переменной, инструкции SQL, хранимой процедуры, имя таблицы, URL-адрес или полное путь имя файла. Если *источника* — это путь к имени файла, он может быть полный путь («c:\dir\file.rst»), относительный путь (».. \file.RST»), или URL-адрес (»<https://files/file.rst>«).  
  
 Не рекомендуется использовать *источника* аргумент **откройте** метод для выполнения запроса, не возвращающих записи, так как нет простого способа определить, успешно ли выполнен вызов. **Записей** возвращается такой запрос будет закрыт. Чтобы выполнить запрос, который не возвращает записи, например инструкцию SQL INSERT, вызовите [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод **команда** объекта или [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод [Подключения](../../../ado/reference/ado-api/connection-object-ado.md) вместо этого объекта.  
  
 *ActiveConnection* аргумент соответствует [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойства и указывает, в какое подключение, чтобы открыть **записей** объекта. Если передать определение подключения для этого аргумента, ADO открывает новое подключение, используя указанные параметры. После открытия **записей** с клиентский курсор, задав [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**, можно изменить значение этого свойства для отправки обновления для другого поставщика. Или можно присвоить этому свойству **ничего не** (в Microsoft Visual Basic) или значение NULL, чтобы отключить **записей** из любого поставщика. Изменение *ActiveConnection* для серверного курсора приводит к ошибке, однако.  
  
 Для других аргументов, которые соответствуют свойствам **записей** объекта (*источника*, *CursorType*, и *LockType*), связь аргументов к свойствам выглядит следующим образом:  
  
-   Свойство доступно для чтения/записи, перед **записей** объект открыт.  
  
-   Параметры используются только при проведении соответствующие аргументы при выполнении **откройте** метод. Если передать аргумент, он переопределяет значение соответствующего свойства и значения этого свойства обновляется значение аргумента.  
  
-   После открытия **записей** объекта, эти свойства становятся доступными только для чтения.  
  
> [!NOTE]
>  **ActiveConnection** свойство доступно только для чтения для **записей** объектов, [источника](../../../ado/reference/ado-api/source-property-ado-recordset.md) задано допустимое **команда** объекта, даже если **записей** объектов не открыт.  
  
 При передаче **команда** объекта в *источника* аргумента, а также pass *ActiveConnection* аргумент, возникает ошибка. **ActiveConnection** свойство **команда** объект должен уже быть задано допустимое **подключения** объект или строка подключения.  
  
 Если передать что-то отличное от **команда** объекта в *источника* аргумент, можно использовать *параметры* аргумент для оптимизации вычисление *источника*  аргумент. Если *параметры* аргумент не задан, могут возникать снижение производительности, так как ADO необходимо выполнять вызовы к поставщику для определения того, является ли аргумент инструкции SQL, хранимая процедура, URL-адрес или имя таблицы. Если вы знаете, что *источника* тип используется, установка *параметры* аргумент указывает ADO для перехода непосредственно к соответствующему коду. Если *параметры* аргумент не соответствует *источника* типа, возникает ошибка.  
  
 Если передать **Stream** объекта в *источника* аргумент, не следует передавать сведения в других аргументов. Это приведет к ошибке. **ActiveConnection** информация не сохраняется при **записей** открывается из **Stream**.  
  
 По умолчанию для *параметры* аргумент **adCmdFile** Если подключение не связан с классом **записей**. Обычно это будет так для постоянно храниться **записей** объектов.  
  
 Если источник данных не возвращает записи, то поставщик устанавливает оба [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) и [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойства **True**, и текущего положения записи не определено. По-прежнему можно добавлять новые данные на этом пустой **записей** объекта, если тип курсора позволяет ей.  
  
 После завершения операции через открытый **записей** , используйте [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод, чтобы освободить все связанные с ним ресурсы системы. Закрыть объект не удаляется из памяти; Вы можете изменить настройки его свойств и использовать **откройте** метод, чтобы открыть его позже. Чтобы полностью исключить объект из памяти, присвоить переменной объекта *ничего не*.  
  
 Перед **ActiveConnection** свойству, вызовите **откройте** с операндами, не для создания экземпляра **записей** создан путем добавления полей к  **Набор записей** [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции.  
  
 Если вы задали [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**, можно получить строки асинхронно в одном из двух способов. Рекомендуется задать *параметры* для **adAsyncFetch**. Кроме того, можно использовать «Asynchronous Processing набора строк» динамическое свойство в [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции, но связанных событий, полученных могут быть потеряны, если не задано *параметры* параметр **adAsyncFetch**.  
  
> [!NOTE]
>  Получение фона в поставщике MS удаленного поддерживается только при помощи **откройте** метода *параметры* параметра.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Определенные сочетания [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) и [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения не являются допустимыми. Сведения о том, какие параметры нельзя использовать вместе, см. в разделах [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md), и [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Open и Close (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Примеры методов Open и Close (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Примеры методов Open и Close (Visual C++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Сохранение и открытие примеры методов (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)

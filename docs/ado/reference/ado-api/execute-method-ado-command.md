---
title: Выполнение метода (объект Command ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Execute
- Command15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: f84a5ff3-0528-4ad7-9bea-9a15103378dd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 88718c492702018b77e89597faec8897aa8f51f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697923"
---
# <a name="execute-method-ado-command"></a>Метод Execute (объект Command ADO)
Выполняет запрос, инструкции SQL или хранимой процедуры, которая указана в [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) свойство [объект команды](../../../ado/reference/ado-api/command-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) ссылку на объект, поток, или **ничего не**.  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Необязательный параметр. Объект **Long** переменной, в которой поставщик возвращает количество записей, затронутых операцией. *RecordsAffected* параметр применяется только для запросов или хранимых процедур. *RecordsAffected* не возвращает число записей, возвращенных в возвращающих результат запроса или хранимой процедуры. Чтобы получить эти сведения, используйте [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) свойство. **Execute** метод не возвращает правильные данные при использовании с **adAsyncExecute**, просто потому, что при выполнении команды асинхронно, количество обработанных записей еще неизвестна во время выполнения метода.  
  
 *Параметры*  
 Необязательный. Объект **Variant** массив значений параметров, используется в сочетании с входную строку или поток, указанный в **CommandText** или **CommandStream**. (Выходные параметры не вернет правильные значения при передаче в этом аргументе.)  
  
 *Параметры*  
 Необязательный. Объект **Long** значение, указывающее, каким образом следует оценить, поставщик [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) свойство [команда](../../../ado/reference/ado-api/command-object-ado.md) объект. Может представлять собой значение битовой маски, выполненные с помощью [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) и/или [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения. Например, можно использовать **adCmdText** и **adExecuteNoRecords** в сочетании, если требуется, чтобы оценить значение ADO **CommandText** свойство как текст, и Укажите, что команда должна отменить и не возвратит никаких записей, которые могут возникнуть при выполнении текст команды.  
  
> [!NOTE]
>  Используйте **ExecuteOptionEnum** значение **adExecuteNoRecords** для повышения производительности, сводя к минимуму внутренней обработки. Если **adExecuteStream** был указан, параметры **adAsyncFetch** и **adAsynchFetchNonBlocking** игнорируются. Не используйте **CommandTypeEnum** значения **adCmdFile** или **adCmdTableDirect** с **Execute**. Эти значения могут использоваться только как параметры с [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery](../../../ado/reference/ado-api/requery-method.md) методы **записей**.  
  
## <a name="remarks"></a>Примечания  
 С помощью **Execute** метод **команда** выполняется запрос, указанный в объект **CommandText** свойство или **CommandStream** свойство объекта.  
  
 Результаты возвращаются в **записей** (по умолчанию) или в виде потока двоичных данных. Чтобы получить двоичный поток, задайте **adExecuteStream** в *параметры*, затем указать поток, задав **Command.Properties («выходные данные Stream")** . ADO **Stream** объекта может быть указано для получения результатов, или другой объект stream, такие как объект ответа службы IIS могут быть указаны. Если поток не был указан перед вызовом **Execute** с **adExecuteStream**, возникает ошибка. Позицию в потоке при возврате из **Execute** зависит от поставщика.  
  
 Если команда не предназначен для возврата результатов (например, запроса SQL UPDATE) поставщик возвращает **ничего не** условии, что параметр **adExecuteNoRecords** указан; в противном случае Execute которого возвращает Закрыто **записей**. В некоторых языках приложения дают возможность игнорировать это возвращаемое значение, если не **записей** требуется.  
  
 **Выполнение** вызывает ошибку, если пользователь указывает значение для **CommandStream** при **CommandType** — **adCmdStoredProc**,  **adCmdTable**, или **adCmdTableDirect**.  
  
 Если запрос содержит параметры, текущего значения для **команда** объекта параметры используются в том случае, если не переопределено с помощью значения параметров, передаваемые с **Execute** вызова. Подмножество этих параметров можно переопределить, опустив новые значения для некоторых параметров, при вызове **Execute** метод. Порядок, в котором можно задать параметры — это том же порядке, в котором метод передает их. Например, если существуют четыре (или более) параметры и вы хотите передать новые значения для только первый и четвертый параметры, следует передавать `Array(var1,,,var4)` как *параметры* аргумент.  
  
> [!NOTE]
>  Выходные параметры не вернет правильные значения при передаче в *параметры* аргумент.  
  
 [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) событий будут выдаваться при завершении этой операции.  
  
> [!NOTE]
>  При выдаче команды, содержащие URL-адреса, которые используют схему http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [EXECUTE, Requery и Clear методы (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [EXECUTE, Requery и Clear методы (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [EXECUTE, Requery и Clear методы (Visual C++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Выполнение метода (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Событие ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)

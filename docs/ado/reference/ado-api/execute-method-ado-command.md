---
title: "Выполнить метод (команда ADO) | Документы Microsoft"
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
- Command15::Execute
- Command15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: f84a5ff3-0528-4ad7-9bea-9a15103378dd
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 651123d3112ca58c028412bd025325f303f0d637
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="execute-method-ado-command"></a>Выполнить метод (команда ADO)
Выполняет запрос, инструкции SQL или хранимой процедуры, указанной в [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) свойство [объект команды](../../../ado/reference/ado-api/command-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) ссылка на объект, потока или **ничего не**.  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Необязательно. Объект **длинные** переменной, в которой поставщик возвращает количество записей, затронутых операцию. *RecordsAffected* параметр применяется только для запросов или хранимых процедур. *RecordsAffected* не возвращает число записей, возвращаемых возвращение результата запроса или хранимой процедуры. Для получения этих сведений следует использовать [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) свойство. **Execute** метод не возвращает правильные данные при использовании с **adAsyncExecute**, просто потому, что если команда выполняется асинхронно, количество обработанных записей еще неизвестна во время выполнения метода.  
  
 *Параметры*  
 Необязательно. Объект **Variant** массив значений параметров, используемые в сочетании с входную строку или поток, указанный в **CommandText** или **CommandStream**. (Выходные параметры не вернет правильные значения при передаче в этом аргументе.)  
  
 *Параметры*  
 Необязательно. Объект **длинные** значение, указывающее, как следует оценивать поставщик [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) свойство [команда](../../../ado/reference/ado-api/command-object-ado.md) объект. Может представлять собой значение битовой маски, выполненные с помощью [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) и/или [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения. Например, можно использовать **adCmdText** и **adExecuteNoRecords** вместе, если вы хотите использовать ADO оценки значения элемента **CommandText** свойства в виде текста, и Укажите, что команду следует отменить и не возвратит никаких записей, которые могут возникнуть при выполнении текст команды.  
  
> [!NOTE]
>  Используйте **ExecuteOptionEnum** значение **adExecuteNoRecords** для повышения производительности путем минимизации внутренней обработки. Если **adExecuteStream** был указан параметр **adAsyncFetch** и **adAsynchFetchNonBlocking** игнорируются. Не используйте **CommandTypeEnum** значения **adCmdFile** или **adCmdTableDirect** с **Execute**. Эти значения можно использовать только как параметры с [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery](../../../ado/reference/ado-api/requery-method.md) методы **записей**.  
  
## <a name="remarks"></a>Замечания  
 С помощью **Execute** метод **команда** выполняется запрос, указанный в объект **CommandText** свойство или **CommandStream** свойство объекта.  
  
 Результаты возвращаются в **записей** (по умолчанию) или в виде потока двоичных данных. Чтобы получить двоичный поток, задайте **adExecuteStream** в *параметры*, затем указать поток, задав **Command.Properties («поток вывода»)**. ADO **поток** можно указать объект мог получать результаты, или другой объект потока, например объект ответа службы IIS могут быть указаны. Если поток не был указан перед вызовом **Execute** с **adExecuteStream**, возникает ошибка. Позиция в потоке при возврате из **Execute** зависит от поставщика.  
  
 Если команда не является возвращать результаты (например, запрос SQL UPDATE) поставщик возвращает **ничего** , пока параметр **adExecuteNoRecords** указан; в противном случае выполняется возвращает Закрыто **записей**. В некоторых языках приложения позволяют игнорировать это возвращаемое значение, если не **записей** требуется.  
  
 **Выполнение** вызывает ошибку, если пользователь указывает значение для **CommandStream** при **CommandType** — **adCmdStoredProc**, ** adCmdTable**, или **adCmdTableDirect**.  
  
 Если запрос содержит параметры, текущего значения для **команда** объекта параметры используются в том случае, если не переопределено с помощью значений параметров, передаваемых с **Execute** вызова. Можно переопределить подмножество параметров, не указывайте новые значения для некоторых параметров при вызове **Execute** метод. Порядок, в котором указываются параметры находится в том же порядке, в котором метод передает их. Например, если существуют параметры четыре (или более) и для передачи новых значений только первый и четвертый параметров, следует передавать `Array(var1,,,var4)` как *параметры* аргумент.  
  
> [!NOTE]
>  Выходные параметры не вернет правильные значения при передаче в *параметры* аргумент.  
  
 [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) события будут выдаваться в случае, когда эта операция завершается.  
  
> [!NOTE]
>  При выдаче команды, содержащие URL-адресов, используемых в схему http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполнение и Requery снимите примере методы (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Выполнение и Requery снимите примере методы (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Выполнение и Requery снимите примере методы (VC ++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Свойства CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Выполнить метод (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Событие ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)


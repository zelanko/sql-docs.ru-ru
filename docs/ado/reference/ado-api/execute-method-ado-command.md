---
description: Метод Execute (объект Command ADO)
title: Метод Execute (команда ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b33ada4ce6ac53c1caafbec80c19d1fd31deb6ab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443896"
---
# <a name="execute-method-ado-command"></a>Метод Execute (объект Command ADO)
Выполняет запрос, инструкцию SQL или хранимую процедуру, указанную в свойстве [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) [объекта Command](../../../ado/reference/ado-api/command-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает ссылку на объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , поток или **ничего**.  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Необязательный параметр. **Длинная** переменная, к которой поставщик возвращает количество записей, затронутых операцией. Параметр *рекордсаффектед* применяется только для запросов действий или хранимых процедур. *Рекордсаффектед* не возвращает число записей, возвращенных запросом, возвращающим результат, или хранимой процедурой. Чтобы получить эти сведения, используйте свойство [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) . Метод **EXECUTE** не возвращает правильные сведения при использовании с **адасинцексекуте**, просто потому, что при асинхронном выполнении команды число затронутых записей может еще не быть известно во время возврата метода.  
  
 *Параметры*  
 Необязательный параметр. Массив **вариантов** значений параметров, используемых в сочетании со входной строкой или потоком, указанным в параметре **CommandText** или **CommandStream**. (Выходные параметры не будут возвращать правильные значения при передаче в этом аргументе.)  
  
 *Параметры*  
 Необязательный параметр. Значение **типа Long** , указывающее, как поставщик должен оценивать свойство [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) или [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) объекта [Command](../../../ado/reference/ado-api/command-object-ado.md) . Может быть значением битовой маски, сделанным с помощью значений [коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md) и/или [ексекутеоптионенум](../../../ado/reference/ado-api/executeoptionenum.md) . Например, можно использовать **адкмдтекст** и **адексекутенорекордс** в сочетании, если предполагается, что ADO вычисляет значение свойства **CommandText** как текст и указывает, что команда должна быть удалена и не возвращать записи, которые могут быть созданы при выполнении текста команды.  
  
> [!NOTE]
>  Используйте значение **Ексекутеоптионенум** **адексекутенорекордс** для повышения производительности за счет минимизации внутренней обработки. Если указан параметр **адексекутестреам** , параметры **адасинкфетч** и **адасинчфетчнонблоккинг** игнорируются. Не используйте значения **коммандтипинум** для **адкмдфиле** или **адкмдтабледирект** с **EXECUTE**. Эти значения можно использовать только в качестве параметров с методами [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery](../../../ado/reference/ado-api/requery-method.md) **набора записей**.  
  
## <a name="remarks"></a>Remarks  
 При использовании метода **EXECUTE** для объекта **Command** выполняется запрос, указанный в свойстве **CommandText** или в свойстве **CommandStream** объекта.  
  
 Результаты возвращаются в **наборе записей** (по умолчанию) или в виде потока двоичных данных. Чтобы получить двоичный поток, укажите **адексекутестреам** в *параметрах*, а затем укажите поток, задав **команду. Properties ("поток вывода")**. Для получения результатов можно указать объект **потока** ADO или указать другой объект потока, например объект ответа IIS. Если перед вызовом **EXECUTE** с **адексекутестреам**не был указан поток, возникает ошибка. Расположение потока при возврате из **EXECUTE** зависит от конкретного поставщика.  
  
 Если команда не должна возвращать результаты (например, запрос SQL UPDATE), поставщик возвращает **значение Nothing** , если указан параметр **адексекутенорекордс** . в противном случае Execute возвращает закрытый **набор записей**. Некоторые языки приложений позволяют игнорировать это возвращаемое значение, если **набор записей** не требуется.  
  
 **EXECUTE** выдает ошибку, если пользователь указывает значение для **CommandStream** , если **CommandType** — **адкмдсторедпрок**, **адкмдтабле**или **адкмдтабледирект**.  
  
 Если запрос содержит параметры, используются текущие значения параметров **командного** объекта, если только они не переопределены значениями параметров, передаваемыми при вызове **EXECUTE** . Можно переопределить подмножество параметров, опустив новые значения для некоторых параметров при вызове метода **EXECUTE** . Порядок, в котором указываются параметры, совпадает с порядком, в котором метод передает их. Например, при наличии четырех (или более) параметров и необходимости передачи новых значений только для первого и четвертого параметров необходимо передать в `Array(var1,,,var4)` качестве аргумента *параметров* .  
  
> [!NOTE]
>  Выходные параметры не будут возвращать правильные значения при передаче в аргумент *параметров* .  
  
 Когда эта операция завершается, будет выдано событие [ексекутекомплете](../../../ado/reference/ado-api/executecomplete-event-ado.md) .  
  
> [!NOTE]
>  При выдаче команд, содержащих URL-адреса, при использовании схемы HTTP автоматически вызывается [поставщик Microsoft OLE DB для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов Execute, Requery и Clear (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Пример методов Execute, Requery и Clear (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Пример методов Execute, Requery и Clear (Visual c++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Метод Execute (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Событие ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)

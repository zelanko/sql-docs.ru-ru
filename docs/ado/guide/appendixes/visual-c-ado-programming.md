---
title: Visual C++ программирование ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO]
ms.assetid: 11233b96-e05c-4221-9aed-5f20944b0f1c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1890d554367b2a21bcd46a6d2ebddf00013957e6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926421"
---
# <a name="visual-c-ado-programming"></a>Программирование объектов ADO с использованием Visual C++
Справочник по API ADO описывает функциональные возможности интерфейса прикладного программирования (API) ADO, используя синтаксис, аналогичный Microsoft Visual Basic. Хотя предполагаемая аудитория — все пользователи, программисты ADO используют различные языки, такие как Visual Basic, Visual C++ (с директивой **#import** и без нее) и Visual J++ (с пакетом класса ADO/WFC).  

> [!NOTE]
> Корпорация Майкрософт прекратила поддержку Visual J++ в 2004.

 Для обеспечения этого разнообразия [Visual C++ индексы синтаксиса ADO](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) предоставляют Visual C++ синтаксис для конкретного языка со ссылками на общие описания функций, параметров, исключительных вариантов поведения и т. д. в справочнике по API.  
  
 ADO реализуется с помощью интерфейсов COM (объектная модель компонентов). Однако программистам проще работать с COM в определенных языках программирования, чем в других. Например, почти все детали использования COM обрабатываются неявно для Visual Basic программистов, тогда как Visual C++ программистам необходимо принять участие в этих деталях.  
  
 В следующих разделах приводятся сводные сведения для программистов C и C++, использующих ADO и директиву **#import** . Основное внимание уделяется типам данных COM (**Variant**, **BSTR**и **SAFEARRAY**) и обработке ошибок (_com_error).  
  
## <a name="using-the-import-compiler-directive"></a>Использование директивы компилятора #import  
 Директива компилятора **#import** Visual C++ упрощает работу с методами и свойствами ADO. Директива принимает имя файла, содержащего библиотеку типов, например ADO. dll (Msado15. dll), и создает файлы заголовков, содержащие объявления typedef, интеллектуальные указатели для интерфейсов и перечислимые константы. Каждый интерфейс инкапсулируется или упаковывается в класс.  
  
 Для каждой операции в классе (т. е. вызове метода или свойства) существует объявление, которое вызывает операцию напрямую (то есть «необработанная» форма операции), и объявление для вызова необработанной операции и выдает ошибку COM, если операции не удается выполнить сукк ессфулли. Если операция является свойством, то обычно существует директива компилятора, которая создает альтернативный синтаксис для операции, имеющей такой синтаксис, как Visual Basic.  
  
 Операции, излучающие значение свойства, имеют имена в форме, **получить**_свойство_. Операции, устанавливающие значение свойства, имеют имена формы,_свойства_ **размещения**. Операции, которые задают значение свойства с указателем на объект ADO, имеют имена в виде_свойства_ **путреф**.  
  
 Вы можете получить или задать свойство с помощью вызовов следующих форм:  
  
```cpp
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```
  
## <a name="using-property-directives"></a>Использование директив свойств  
 Директива компилятора **__declspec (Property...)** — это расширение языка C, специфическое для Microsoft, которое объявляет функцию, используемую как свойство, для использования альтернативного синтаксиса. В результате можно задать или получить значения свойства так же, как Visual Basic. Например, можно задать и получить свойство следующим образом:  
  
```cpp
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```
  
 Обратите внимание, что вам не нужно выполнять код:  
  
```cpp
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```
  
 Компилятор создаст соответствующий вызов_Свойства_ **Get**_-_, Where **-или** **путреф**, основываясь на объявлении альтернативного синтаксиса и о том, выполняется ли чтение или запись свойства.  
  
 Директива компилятора **__declspec (Property...)** может объявлять **только альтернативный** синтаксис для **функции, например** **Get**, WHERE или **Get** . Операции только для чтения имеют только объявление **Get** ; операции только для записи имеют только объявление « **Размещение** »; операции, доступные для **чтения и записи, имеют объявления** **Get** и WHERE.  
  
 Эта директива может иметь только два объявления. Однако у каждого свойства могут быть три функции свойств: **Получение**_свойства_, **Размещение**_и свойство_ **путреф**_._ В этом случае только две формы свойства имеют альтернативный синтаксис.  
  
 Например, свойство **ActiveConnection** объекта **Command** объявляется с альтернативным синтаксисом для **Get**_ActiveConnection_ и **путреф**_ActiveConnection_. **Путреф**-синтаксис является хорошим выбором, поскольку на практике в этом свойстве обычно требуется поместить открытый объект **соединения** (т. е. указатель объекта **соединения** ). С другой стороны, объект **Recordset** имеет операции **Get** **-, WHERE**-и **путреф**_ActiveConnection_ , но не имеет альтернативного синтаксиса.  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>Коллекции, метод DataItem и свойство Item  

 ADO определяет несколько коллекций, включая **поля**, **Параметры**, **Свойства**и **ошибки**. В Visual C++ метод **Item (_индекс_)** Возвращает элемент коллекции. *Index* — это **вариант**, значение которого является либо числовым индексом элемента в коллекции, либо строкой, содержащей имя элемента.  
  
 Директива компилятора **__declspec (Property...)** объявляет свойство **Item** в качестве альтернативного синтаксиса для каждого основного метода **Item ()** коллекции. Альтернативный синтаксис использует квадратные скобки и похож на ссылку на массив. Как правило, две формы выглядят следующим образом:  
  
```cpp
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```
  
 Например, можно присвоить значение полю объекта **набора записей** с именем **_RS_**, производного от таблицы **authors** базы данных **pubs** . Используйте свойство **Item ()** для доступа к третьему **полю** коллекции **полей** объекта **Recordset** (коллекции индексируются с нуля; Предположим, что третье поле имеет имя **_\_Au fname_**). Затем вызовите метод **value ()** для объекта **field** , чтобы присвоить строковое значение.  
  
 Это можно выразить в Visual Basic следующими четырьмя способами (последние две формы являются уникальными для Visual Basic; другие языки не имеют эквивалентов):  
  
```cpp
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```
  
 Эквивалент в Visual C++ первые две формы выше:  
  
```cpp
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```
  
 -или-(также показан альтернативный синтаксис для свойства **value** )  
  
```cpp
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```
  
 Примеры итераций коллекции см. в разделе "коллекции ADO" статьи "Справочник по ADO".  
  
## <a name="com-specific-data-types"></a>Типы данных, относящиеся к COM  
 Как правило, любой тип данных Visual Basic, который можно найти в справочнике по API ADO, имеет Visual C++ эквивалент. **К ним**относятся стандартные типы данных, например **char без знака** , для Visual Basic **байт**, **Short** для **Integer**и **Long** . Взгляните на синтаксис Индексесто посмотрите, что именно требуется для операндов данного метода или свойства.  
  
 Исключениями из этого правила являются типы данных, характерные для COM: **Variant**, **BSTR**и **SAFEARRAY**.  
  
### <a name="variant"></a>Variant  
 **Вариант** — это структурированный тип данных, который содержит элемент значения и член типа данных. **Вариант** может содержать широкий диапазон других типов данных, включая другой вариант, BSTR, логический, IDispatch или указатель IUnknown, валюту, дату и т. д. COM также предоставляет методы, которые упрощают преобразование одного типа данных в другой.  
  
 Класс **_variant_t** инкапсулирует и управляет типом данных **Variant** .  
  
 Если в справочнике по API ADO указано, что метод или операнд свойства принимает значение, обычно это означает, что значение передается в **_variant_t**.  
  
 Это правило явно истинно, если в разделе **Parameters** справочника по API ADO указано, что операнд является **вариантом**. Единственным исключением является то, что в документации явно указано, что операнд принимает стандартный тип данных, например **Long** или **Byte**, или перечисление. Другое исключение — когда операнд принимает **строку**.  
  
### <a name="bstr"></a>BSTR  
 Тип данных **BSTR** (**B**— это схема, в которой используется **str**). COM предоставляет методы для выделения, обработки и освобождения **BSTR**.  
  
 Класс **_bstr_t** инкапсулирует и управляет типом данных **BSTR** .  
  
 Если в справочнике по API ADO указано, что метод или свойство принимает **строковое** значение, это означает, что значение указано в виде **_bstr_t**.  
  
### <a name="casting-_variant_t-and-_bstr_t-classes"></a>Приведение классов _variant_t и _bstr_t  
 Часто нет необходимости явно кодировать **_variant_t** или **_bstr_t** в аргументе операции. Если класс **_variant_t** или **_bstr_t** имеет конструктор, соответствующий типу данных аргумента, компилятор создаст соответствующий **_variant_t** или **_bstr_t**.  
  
 Однако если аргумент является неоднозначным, то есть тип данных аргумента соответствует более чем одному конструктору, необходимо привести аргумент с соответствующим типом данных для вызова правильного конструктора.  
  
 Например, объявление метода **Recordset:: Open** имеет следующее значение:  
  
```cpp
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```
  
 `ActiveConnection` Аргумент принимает ссылку на **_variant_t**, который можно закодировать как строку подключения или указатель на открытый объект **соединения** .  
  
 Правильное **_variant_t** будет создаваться неявно, если передать строку, такую как "`DSN=pubs;uid=MyUserName;pwd=MyPassword;`", или указатель, например "`(IDispatch *) pConn`".  
  
> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.  
  
 Или вы можете явно закодировать **_variant_t** , содержащий указатель, например "`_variant_t((IDispatch *) pConn, true)`". Приведение, `(IDispatch *)`, разрешает неоднозначность с другим конструктором, принимающим указатель на интерфейс IUnknown.  
  
 Это крайне важный, хотя и редко упоминаемый факт, что ADO является интерфейсом IDispatch. Всякий раз, когда указатель на объект ADO должен быть передан как **Variant**, этот указатель должен быть приведен в качестве указателя на интерфейс IDispatch.  
  
 Последний случай явно кодирует второй логический аргумент конструктора с необязательным значением по умолчанию `true`. Этот аргумент заставляет конструктор **Variant** вызывать метод **AddRef**(), который компенсирует ado автоматический вызов метода **_variant_t:: Release**() при завершении вызова метода или свойства ADO.  
  
### <a name="safearray"></a>SafeArray  
 **SAFEARRAY** — это структурированный тип данных, содержащий массив других типов данных. **Массив SafeArray** называется *типобезопасным* , так как он содержит сведения о границах каждого измерения массива и ограничивает доступ к элементам массива в пределах этих границ.  
  
 Если в справочнике по API ADO указано, что метод или свойство принимает или возвращает массив, это означает, что метод или свойство принимает или возвращает **SAFEARRAY**, а не собственный массив C/C++.  
  
 Например, для второго параметра метода **Connection** объекта **OpenSchema** требуется массив значений **типа Variant** . Эти значения **типа Variant** должны передаваться как элементы массива **SAFEARRAY**, и этот **SAFEARRAY** должен быть задан как значение другого **варианта**. Это значит, что другой **вариант** , передаваемый в качестве второго аргумента **OpenSchema**.  
  
 В качестве дальнейших примеров первым аргументом метода **Find** является **вариант** , значение которого является одномерным **массивом SAFEARRAY**; Каждый необязательный первый и второй аргументы **AddNew** является одномерным **массивом SAFEARRAY**; и возвращаемое значение метода **GetRows** — это **вариант** , значение которого является двумерным **массивом SAFEARRAY**.  
  
## <a name="missing-and-default-parameters"></a>Отсутствующие и параметры по умолчанию  
 Visual Basic допускает отсутствие параметров в методах. Например, метод **Open** объекта **Recordset** имеет пять параметров, но вы можете пропустить промежуточные параметры и выйти из параметров в конце. Значение **BSTR** или **Variant** по умолчанию будет заменено в зависимости от типа данных отсутствующего операнда.  
  
 В C/C++ должны быть указаны все операнды. Если необходимо указать отсутствующий параметр, тип данных которого является строкой, укажите **_bstr_t** , содержащую пустую строку. Если необходимо указать отсутствующий параметр, тип данных которого является **вариантом**, укажите **_variant_t** со значением DISP_E_PARAMNOTFOUND и типом VT_ERROR. Кроме того, можно указать эквивалентную **_variant_t** константу **втмиссинг**, которая предоставляется директивой **#import** .  
  
 Три метода являются исключениями для типичного использования **втмиссинг**. Это методы **EXECUTE** для объектов **Connection** и **Command** , а также метод **NextRecordset** объекта **Recordset** . Ниже приведены их сигнатуры.  
  
```cpp
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```
  
 Параметры *рекордсаффектед* и *Parameters*являются указателями на **Variant**. *Parameters* — это входной параметр, указывающий адрес **варианта** , содержащего один параметр, или массив параметров, который изменяет выполняемую команду. *Рекордсаффектед* — это выходной параметр, указывающий адрес **варианта**, в котором возвращается число строк, затронутых методом.  
  
 В методе **EXECUTE** объекта **Command** укажите, что параметры не указаны, задав для *параметров* значение `&vtMissing` (рекомендуется) или указатель null (то есть **null** или ноль (0)). Если для *параметров* задан нулевой указатель, метод внутренне заменяет эквивалент **втмиссинг**, а затем завершает операцию.  
  
 Во всех методах указывается, что количество затронутых записей не должно возвращаться путем установки *рекордсаффектед* в указатель null. В этом случае пустой указатель не имеет такого значения, как указывает, что метод должен отменить количество затронутых записей.  
  
 Таким образом, для этих трех методов код может быть следующим:  
  
```cpp
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```
  
## <a name="error-handling"></a>Обработка ошибок  
 В COM большинство операций возвращают код возврата HRESULT, указывающий, успешно ли завершилась функция. Директива **#import** создает код-оболочку вокруг каждого "необработанного" метода или свойства и проверяет ВОЗВРАЩЕННОЕ значение HRESULT. Если HRESULT указывает на сбой, код программы-оболочки вызывает ошибку COM путем вызова _com_issue_errorex () с кодом возврата HRESULT в качестве аргумента. Объекты ошибок COM могут быть перехвачены в блоке **try**-**catch** . (Для повышения эффективности перехватите ссылку на объект **_com_error** .)  
  
 Помните, что это ошибки ADO: они вызваны сбоем операции ADO. Ошибки, возвращенные базовым поставщиком, отображаются как объекты **ошибок** в коллекции **ошибок** объектов **соединения** .  
  
 Директива **#import** создает только подпрограммы обработки ошибок для методов и свойств, объявленных в ADO. dll. Тем не менее можно воспользоваться тем же механизмом обработки ошибок, написав собственный макрос или встроенную функцию проверки ошибок. Примеры см. в разделе [Visual C++ расширениях](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md)или коде в следующих разделах.  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Visual C++ эквиваленты соглашений Visual Basic  
 Ниже приведена сводка по нескольким соглашениям в документации ADO, закодированных в Visual Basic, а также их эквиваленты в Visual C++.  
  
### <a name="declaring-an-ado-object"></a>Объявление объекта ADO  
 В Visual Basic объектная переменная ADO (в данном случае для объекта **Recordset** ) объявляется следующим образом:  
  
```vb
Dim rst As ADODB.Recordset  
```
  
 Предложение "`ADODB.Recordset`" является идентификатором ProgID объекта **набора записей** , как определено в реестре. Новый экземпляр объекта **Record** объявляется следующим образом:  
  
```vb
Dim rst As New ADODB.Recordset  
```
  
 -или-  
  
```vb
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```
  
 В Visual C++ директива **#import** создает объявления интеллектуального типа указателя для всех объектов ADO. Например, переменная, указывающая на объект **_Recordset** , имеет тип **_RecordsetPtr**и объявляется следующим образом:  
  
```cpp
_RecordsetPtr  rs;  
```
  
 Переменная, указывающая на новый экземпляр объекта **_Recordset** , объявляется следующим образом:  
  
```cpp
_RecordsetPtr  rs("ADODB.Recordset");  
```
  
 -или-  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance("ADODB.Recordset");  
```
  
 -или-  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance(__uuidof(_Recordset));  
```
  
 После вызова метода **CreateInstance** переменную можно использовать следующим образом:  
  
```cpp
rs->Open(...);  
```
  
 Обратите внимание, что в одном случае`.`оператор "" используется, как если бы переменная была экземпляром класса (`rs.CreateInstance`), а в другом случае оператор "`->`" используется, как если бы переменная была указателем на интерфейс (`rs->Open`).  
  
 Одну переменную можно использовать двумя способами, так как оператор`->`"" перегружен, чтобы позволить экземпляру класса вести себя как указатель на интерфейс. Частный член класса переменной экземпляра содержит указатель на интерфейс **_Recordset** ; оператор "`->`" возвращает этот указатель; и возвращаемый указатель обращается к членам объекта **_Recordset** .  
  
### <a name="coding-a-missing-parameter---string"></a>Написание кода для отсутствующей строки параметра  
 Если необходимо закодировать отсутствующий **строковый** операнд в Visual Basic, то операнд просто опускается. Необходимо указать операнд в Visual C++. Код **_bstr_t** , имеющий пустую строку в качестве значения.  
  
```cpp
_bstr_t strMissing(L"");  
```
  
### <a name="coding-a-missing-parameter---variant"></a>Написание кода для пропущенного параметра-Variant  
 Если необходимо закодировать отсутствующий операнд **типа Variant** в Visual Basic, то операнд просто опускается. Необходимо указать все операнды в Visual C++. В коде отсутствует параметр **Variant** с **_variant_t** , для которого задано специальное значение, DISP_E_PARAMNOTFOUND и тип, VT_ERROR. Кроме того, можно указать **втмиссинг**, которая является эквивалентной предопределенной константой, предоставляемой директивой **#import** .  
  
```cpp
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```
  
 -или use-  
  
```cpp
...vtMissing...;  
```
  
### <a name="declaring-a-variant"></a>Объявление варианта  
 В Visual Basic **тип Variant** объявляется с помощью оператора **Dim** следующим образом:  
  
```vb
Dim VariableName As Variant  
```
  
 В Visual C++ объявите переменную как **_variant_t**типа. Ниже показаны несколько схематических **_variant_t** объявлений.  
  
> [!NOTE]
>  Эти объявления просто придают грубое представление о том, что вы намерены программировать в собственной программе. Дополнительные сведения см. в примерах ниже и в документации по Visual C + +.  
  
```cpp
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```
  
### <a name="using-arrays-of-variants"></a>Использование массивов вариантов  
 В Visual Basic массивы типа **Variant** можно закодировать оператором **Dim** или использовать функцию **Array** , как показано в следующем примере кода:  
  
```vb
Public Sub ArrayOfVariants  
Dim cn As ADODB.Connection  
Dim rs As ADODB.Recordset  
Dim fld As ADODB.Field  
  
    cn.Open "DSN=pubs"  
    rs = cn.OpenSchema(adSchemaColumns, _  
        Array(Empty, Empty, "authors", Empty))  
    For Each fld in rs.Fields  
        Debug.Print "Name = "; fld.Name  
    Next fld  
    rs.Close  
    cn.Close  
End Sub  
```
  
 В следующем примере Visual C++ демонстрируется использование **массива SafeArray** , используемого с **_variant_t**.  
  
#### <a name="notes"></a>Заметки  
 Следующие примечания соответствуют подразделам с комментариями в примере кода.  
  
1.  Опять же, встроенная функция ТЕССР () определяется для использования преимуществ существующего механизма обработки ошибок.  
  
2.  Нужен только одномерный массив, поэтому можно использовать **сафеаррайкреатевектор**вместо объявления общего назначения **Сафеаррайбаунд** и функции **сафеаррайкреате** . Ниже приведен код, который будет выглядеть с помощью **сафеаррайкреате**:  
  
    ```cpp
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```
  
3.  Схема, идентифицируемая перечислимой константой **адсчемаколумнс**, связана с четырьмя столбцами ограничений: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME и column_name. Поэтому создается массив значений **типа Variant** с четырьмя элементами. Затем указывается значение ограничения, соответствующее третьему столбцу, TABLE_NAME.  
  
     Возвращаемый **набор записей** состоит из нескольких столбцов, подмножество которых является столбцами ограничений. Значения столбцов ограничений для каждой возвращаемой строки должны совпадать со значениями соответствующих ограничений.  
  
4.  Те, кто знаком с **SAFEARRAY** , могут быть удивлены тем, что **сафеаррайдестрой**() не вызывается перед выходом. Фактически вызов **сафеаррайдестрой**() в этом случае приведет к возникновению исключения времени выполнения. Причина заключается в том, что деструктор `vtCriteria` для будет вызывать **вариантклеар**(), когда **_variant_t** выходит из области, что освобождает **SAFEARRAY**. Вызов **сафеаррайдестрой**без ручного очистки **_variant_t**приведет к тому, что деструктор попытается очистить недопустимый указатель **SAFEARRAY** .  
  
     Если были вызваны **сафеаррайдестрой** , код будет выглядеть следующим образом:  
  
    ```cpp
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```
  
     Однако гораздо проще разрешить **_variant_t** управлять **SAFEARRAY**.  
  
```cpp
// Visual_CPP_ADO_Prog_1.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Note 1  
inline void TESTHR( HRESULT _hr ) {   
   if FAILED(_hr)   
      _com_issue_error(_hr);   
}  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _RecordsetPtr pRs("ADODB.Recordset");  
      _ConnectionPtr pCn("ADODB.Connection");  
      _variant_t vtTableName("authors"), vtCriteria;  
      long ix[1];  
      SAFEARRAY *pSa = NULL;  
  
      pCn->Provider = "sqloledb";  
      pCn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
      // Note 2, Note 3  
      pSa = SafeArrayCreateVector(VT_VARIANT, 1, 4);  
      if (!pSa)   
         _com_issue_error(E_OUTOFMEMORY);  
  
      // Specify TABLE_NAME in the third array element (index of 2).   
      ix[0] = 2;        
      TESTHR(SafeArrayPutElement(pSa, ix, &vtTableName));  
  
      // There is no Variant constructor for a SafeArray, so manually set the   
      // type (SafeArray of Variant) and value (pointer to a SafeArray).  
  
      vtCriteria.vt = VT_ARRAY | VT_VARIANT;  
      vtCriteria.parray = pSa;  
  
      pRs = pCn->OpenSchema(adSchemaColumns, vtCriteria, vtMissing);  
  
      long limit = pRs->GetFields()->Count;  
      for ( long x = 0 ; x < limit ; x++ )  
         printf( "%d: %s\n", x + 1, ((char*) pRs->GetFields()->Item[x]->Name) );  
      // Note 4  
      pRs->Close();  
      pCn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Error:\n");  
      printf("Code = %08lx\n", e.Error());  
      printf("Code meaning = %s\n", (char*) e.ErrorMessage());  
      printf("Source = %s\n", (char*) e.Source());  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   CoUninitialize();  
}  
```
  
### <a name="using-property-getputputref"></a>Использование свойства Get/WHERE/Путреф  
 В Visual Basic имя свойства не уточняется, когда оно извлекается, назначается или присваивается ссылка.  
  
```vb
Public Sub GetPutPutRef  
Dim rs As New ADODB.Recordset  
Dim cn As New ADODB.Connection  
Dim sz as Integer  
cn.Open "Provider=sqloledb;Data Source=yourserver;" & _  
         "Initial Catalog=pubs;Integrated Security=SSPI;"  
rs.PageSize = 10  
sz = rs.PageSize  
rs.ActiveConnection = cn  
rs.Open "authors",,adOpenStatic  
' ...  
rs.Close  
cn.Close  
End Sub  
```
  
 В этом Visual C++ примере демонстрируется_свойство_ **Get**/****/**путреф**.  
  
#### <a name="notes"></a>Заметки  
 Следующие примечания соответствуют подразделам с комментариями в примере кода.  
  
1.  В этом примере используются две формы отсутствующего строкового аргумента: явная константа, **стрмиссинг**и строка, которую компилятор будет использовать для создания временного **_bstr_t** , который будет существовать для области действия метода **Open** .  
  
2.  Необязательно приведение операнда `rs->PutRefActiveConnection(cn)` к `(IDispatch *)` , так как тип операнда уже существует. `(IDispatch *)`  
  
```cpp
// Visual_CPP_ado_prog_2.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _bstr_t strMissing(L"");  
      long oldPgSz = 0, newPgSz = 5;  
  
      // Note 1  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", strMissing, "", adConnectUnspecified);  
  
      oldPgSz = rs->GetPageSize();  
      // -or-  
      // oldPgSz = rs->PageSize;  
  
      rs->PutPageSize(newPgSz);  
      // -or-  
      // rs->PageSize = newPgSz;  
  
      // Note 2  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockReadOnly, adCmdTable);  
      printf("Original pagesize = %d, new pagesize = %d\n", oldPgSz, rs->GetPageSize());  
      rs->Close();  
      cn->Close();  
  
   }  
   catch (_com_error &e) {  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```
  
### <a name="using-getitemx-and-itemx"></a>Использование метода DataItem (x) и элемента [x]  
 В этом Visual Basic примере показан стандартный и альтернативный синтаксис для **Item**().  
  
```vb
Public Sub GetItemItem  
Dim rs As New ADODB.Recordset  
Dim name as String  
rs = rs.Open "authors", "DSN=pubs;", adOpenDynamic, _  
         adLockBatchOptimistic, adTable  
name = rs(0)  
' -or-  
name = rs.Fields.Item(0)  
rs(0) = "Test"  
rs.UpdateBatch  
' Restore name  
rs(0) = name  
rs.UpdateBatch  
rs.Close  
End Sub  
```
  
 В этом Visual C++ примере демонстрируется **элемент**.  
  
> [!NOTE]
>  Следующее примечание соответствует подразделам с комментариями в примере кода: когда доступ к коллекции осуществляется с помощью **элемента**, индекс, **2**, должен быть приведен к типу **Long** , поэтому будет вызван соответствующий конструктор.  
  
```cpp
// Visual_CPP_ado_prog_3.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
void main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _variant_t vtFirstName;  
  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", "", "", adConnectUnspecified);  
  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockOptimistic, adCmdTable);  
      rs->MoveFirst();  
  
      // Note 1. Get a field.  
      vtFirstName = rs->Fields->GetItem((long)2)->GetValue();  
      // -or-  
      vtFirstName = rs->Fields->Item[(long)2]->Value;  
  
      printf( "First name = '%s'\n", (char*)( (_bstr_t)vtFirstName) );  
  
      rs->Fields->GetItem((long)2)->Value = L"TEST";  
      rs->Update(vtMissing, vtMissing);  
  
      // Restore name  
      rs->Fields->GetItem((long)2)->PutValue(vtFirstName);  
      // -or-  
      rs->Fields->GetItem((long)2)->Value = vtFirstName;  
      rs->Update(vtMissing, vtMissing);  
      rs->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>Приведение указателей объектов ADO с помощью (IDispatch *)  
 В следующем примере Visual C++ демонстрируется использование (IDispatch *) для приведения указателей объектов ADO.  
  
#### <a name="notes"></a>Заметки  
 Следующие примечания соответствуют подразделам с комментариями в примере кода.  
  
1.  Укажите открытый объект **соединения** в явно закодированном **варианте**. Приведите его к ( \*IDispatch), чтобы вызвать правильный конструктор. Кроме того, явно задайте для второго параметра **_variant_t** значение по умолчанию **true**, поэтому счетчик ссылок на объекты будет правильным, когда заканчивается операция **Recordset:: Open** .  
  
2.  `(_bstr_t)`Выражение,, не является приведением, а **_variant_t** оператором, который извлекает **_bstr_tную** строку из **варианта** , возвращаемого по **значению**.  
  
 Выражение, `(char*)`, не является приведением, а **_bstr_t** оператором, который извлекает указатель на инкапсулированную строку в **_bstr_t** объекте.  
  
 В этом разделе кода демонстрируются некоторые из полезных поведений операторов **_variant_t** и **_bstr_t** .  
  
```cpp
// Visual_CPP_ado_prog_4.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr pConn("ADODB.Connection");  
      _RecordsetPtr pRst("ADODB.Recordset");  
  
      pConn->Provider = "sqloledb";  
      pConn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
  
      // Note 1.  
      pRst->Open("authors", _variant_t((IDispatch *) pConn, true), adOpenStatic, adLockReadOnly, adCmdTable);  
      pRst->MoveLast();  
  
      // Note 2.  
      printf("Last name is '%s %s'\n",   
         (char*) ((_bstr_t) pRst->GetFields()->GetItem("au_fname")->GetValue()),  
         (char*) ((_bstr_t) pRst->Fields->Item["au_lname"]->Value));  
  
      pRst->Close();  
      pConn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }     
   ::CoUninitialize();  
}  
```

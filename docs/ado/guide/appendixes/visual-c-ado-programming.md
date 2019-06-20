---
title: ADO программирования на Visual C++ | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: c8145b4000a621ecb09abff074e4b5e06aea7c80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702617"
---
# <a name="visual-c-ado-programming"></a>Программирование объектов ADO с использованием Visual C++
Справочник по API ADO представлены функции ADO интерфейс программирования (API) с помощью синтаксиса для Microsoft Visual Basic. То, что целевая аудитория всем пользователям, программистам ADO использовать разных языков, например Visual Basic, Visual C++ (с и без **#import** директивы) и Visual J ++ (с пакетом класс ADO и WFC).  

> [!NOTE]
> Microsoft завершилась поддержка для Visual J ++ в 2004 г.

 Для размещения этого разнообразия [ADO для Visual C++ синтаксис индексов](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) предоставляют синтаксис конкретного языка Visual C++ со ссылками на общие описания функциональности, параметров, исключительных поведений и т. д., в API Ссылка.  
  
 ADO реализуется с помощью интерфейсов COM (модель). Однако проще программистам работать с COM на некоторых языках программирования, чем другие. Например почти все подробности использования COM обрабатываются неявно для программистов Visual Basic, в то время как программистам Visual C++ должна посетить к подробностям, сами.  
  
 В следующих разделах приведены сведения для программистов C и C++, с помощью ADO и **#import** директива. В ней описываются типы данных, относящиеся к COM (**Variant**, **BSTR**, и **SafeArray**) и обработка ошибок (_com_error).  
  
## <a name="using-the-import-compiler-directive"></a>С помощью компилятора директива #import  
 **#Import** директивы компилятора Visual C++ упрощает работу с ADO методы и свойства. Директива принимает имя файла, содержащего библиотеку типов, таких как ADO DLL-файл (Msado15.dll) и создает файлы заголовков, содержащие объявления typedef, интеллектуальные указатели для интерфейсов и констант-перечислителей. Каждый интерфейс инкапсулированные или упаковки в классе.  
  
 Для каждой операции в пределах класса (то есть вызов метода или свойства) отсутствует объявление для вызова операции напрямую (то есть «сырой» форме операции) и объявления, чтобы вызвать операцию необработанные и выдавать ошибку COM, если операцию не удается выполнить succ essfully. Если операция является свойством, нет обычно директивы компилятора, который создает альтернативный синтаксис для операции с синтаксисом Visual Basic.  
  
 Операции, которые получают значения свойства имеют имена вида, **получить**_свойство_. Операции, которые задают значение свойства имеют имена вида, **поместить**_свойство_. Операциях, устанавливающих значения свойства с указателем на объект ADO имеют имена вида, **PutRef**_свойство_.  
  
 Вы можете получить или задать свойство с вызовами из этих форм:  
  
```cpp
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```
  
## <a name="using-property-directives"></a>Свойство директив using  
 **__Declspec(property...)**  директивы компилятора является расширением языка C, характерные для Майкрософт, которое объявляет функцию, которая используется как свойство, чтобы альтернативный синтаксис. Таким образом можно задать или получить значения свойства в виде, аналогичную Visual Basic. Например можно задать и получить свойство таким образом:  
  
```cpp
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```
  
 Обратите внимание, что у вас нет к коду:  
  
```cpp
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```
  
 Компилятор создает соответствующий **получить** _-_ , **поместить**-, или **PutRef**_свойство_ звонок, основываясь на какие альтернативный синтаксис объявлен и выполняется ли свойство чтения или записи.  
  
 **__Declspec(property...)**  директивы компилятора можно объявлять только **получить**, **поместить**, или **получить** и **поместить** альтернативный синтаксис для функции. Достаточно только операции чтения **получить** объявлена; только для записи операций, которые имеют только **поместить** объявлена; операции, которые являются оба чтение и запись, иметь оба **получить** и **поместить** объявления.  
  
 С этой директивой; возможны только два объявления Тем не менее каждое свойство может иметь три функции свойств: **Получить**_свойство_, **поместить**_свойство_, и **PutRef**_свойство_. В этом случае только две формы свойства имеют альтернативный синтаксис.  
  
 Например **команда** объект **ActiveConnection** свойство объявлено с альтернативный синтаксис **получить**_ActiveConnection_и **PutRef**_ActiveConnection_. **PutRef**-синтаксис не подходит, поскольку на практике обычно требуется поместить открытый **подключения** объект (то есть **подключения** указатель на объект) в этом свойство. С другой стороны **записей** объект имеет **получить**-, **поместить**-, и **PutRef**_ActiveConnection_операции, но не альтернативный синтаксис.  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>Коллекции, метод GetItem и свойство элемента  

 ADO определяет несколько коллекций, включая **поля**, **параметры**, **свойства**, и **ошибки**. В Visual C++ **GetItem (_индекс_)** методом является членом коллекции. *Индекс* — **Variant**, значение которого является числовой индекс элемента в коллекции, или строка, содержащая имя элемента.  
  
 **__Declspec(property...)**  объявляет директивы компилятора **элемент** свойство как альтернативный синтаксис для каждой коллекции фундаментальные **GetItem() для удаленного элемента** метод. Альтернативный синтаксис используются квадратные скобки и будет выглядеть ссылки на массив. Как правило две формы выглядеть следующим образом:  
  
```cpp
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```
  
 Например, назначить значение к полю **записей** объект, с именем  **_rs_** , который является производным от **авторы** таблицу **pubs** базы данных. Используйте **Item()** свойство для доступа к третий **поле** из **записей** объект **поля** (коллекции, индексируются из коллекции равно нулю; Предположим, третье поле называется  **_au\_fname_** ). Затем вызовите **Value()** метод **поле** для присваивания строковое значение.  
  
 Это можно выразить в Visual Basic в следующих четырех способов (в последних двух форм уникальны для Visual Basic; в других языках не имеют эквивалентов):  
  
```cpp
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```
  
 Является эквивалентом в Visual C++ для первых двух форм выше:  
  
```cpp
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```
  
 \- или - (альтернативный синтаксис **значение** также отображается свойство)  
  
```cpp
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```
  
 Примеры итерации по коллекции см. в разделе «Коллекции ADO», «Справочника ADO».  
  
## <a name="com-specific-data-types"></a>Типы данных COM  
 Как правило любой тип данных Visual Basic, которую вы найдете в справочнике по API ADO имеет эквивалентом Visual C++. К ним относятся стандартные типы данных, такие как **unsigned char** для Visual Basic **байтов**, **короткие** для **целое число**, и  **Long** для **Long**. Поиск в Indexesto синтаксиса см. в разделе именно то, что требуется для операндов заданного метода или свойства.  
  
 Это правило не применяется для COM типы данных: **Variant**, **BSTR**, и **SafeArray**.  
  
### <a name="variant"></a>Variant  
 Объект **Variant** — это тип структурированных данных, содержащий значение и тип элемента данных. Объект **Variant** может содержать широкий спектр типов данных, включая другой вариант, BSTR, логическое значение, IDispatch или IUnknown указатель, валюты, даты и т. д. COM также предоставляет методы, которые позволяют легко преобразовать один тип данных в другой.  
  
 **_Variant_t** класс инкапсулирует и управляет **Variant** тип данных.  
  
 Справочник по API ADO говорит метод или свойство операнд имеет значение, это обычно означает значение, переданное в **_variant_t**.  
  
 Это правило явно значение true, если **параметры** разделе в разделах руководства по API ADO говорит операнд — **Variant**. Единственным исключением является явным образом в документации сказано, операнд принимает тип стандартных данных, таких как **Long** или **байтов**, или перечисления. Другое исключение — когда принимает операнд **строка**.  
  
### <a name="bstr"></a>BSTR  
 Объект **BSTR** (**B**asic **STR**ing) — это тип структурированных данных, содержащий строку символов и длину строки. COM предоставляет методы для выделения, управлять и без **BSTR**.  
  
 **_Bstr_t** класс инкапсулирует и управляет **BSTR** тип данных.  
  
 Когда говорит Справочник по API ADO, метод или свойство принимает **строка** значение он означает, что значение указано в виде **_bstr_t**.  
  
### <a name="casting-variantt-and-bstrt-classes"></a>Приведение классы _variant_t и _bstr_t  
 Часто нет необходимости явно кода **_variant_t** или **_bstr_t** в аргументе операции. Если **_variant_t** или **_bstr_t** класс имеет конструктор, который совпадает с типом данных аргумента, компилятор выдаст соответствующее **_variant_t** или **_bstr_t**.  
  
 Тем не менее если аргумент является неоднозначным, то есть тип данных аргумента соответствует более одного конструктора, аргумент должен быть приведен с помощью соответствующего типа данных для вызова надлежащий конструктор.  
  
 Например, объявление **Recordset::Open** метод:  
  
```cpp
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```
  
 `ActiveConnection` Аргумента принимает ссылку на **_variant_t**, который может кода как строку подключения или указатель на открытый **подключения** объекта.  
  
 Правильный **_variant_t** будет создан неявно при передаче строки, такие как "`DSN=pubs;uid=MyUserName;pwd=MyPassword;`«, или указатель, такие как"`(IDispatch *) pConn`«.  
  
> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.  
  
 Или может явно создавать код **_variant_t** содержащий указатель, такие как "`_variant_t((IDispatch *) pConn, true)`«. Приведение, `(IDispatch *)`, устраняет неоднозначности с другой конструктор, который принимает указатель на интерфейс IUnknown.  
  
 Очень важно, хотя редко упоминалось факт, что ADO — это интерфейс IDispatch. Каждый раз, когда указатель на объект ADO должен быть передан в качестве **Variant**, этому указателю должен быть приведен как указатель на интерфейс IDispatch.  
  
 Последний случай явно коды второй аргумент логического конструктора с необязательным, значение по умолчанию `true`. Этот аргумент вынуждает **Variant** конструктор для вызова его **AddRef**метод (), который компенсирует ADO автоматический вызов **_variant_t::Release**метод) После завершения вызова метода или свойства ADO.  
  
### <a name="safearray"></a>Массив SafeArray  
 Объект **SafeArray** — тип структурированных данных, который содержит массив типов данных. Объект **SafeArray** называется *безопасном* , так как он содержит сведения о границы каждого измерения массива и ограничивает доступ к элементам массива в пределах этих границ.  
  
 Когда Справочник по API ADO говорит метод или свойство принимает или возвращает массив, значит метод или свойство принимает или возвращает **SafeArray**, не собственный массив C/C++.  
  
 Например, второй параметр **подключения** объект **OpenSchema** методу требуется массив **Variant** значения. Те **Variant** значения должны передаваться как элементы **SafeArray**и что **SafeArray** необходимо задать как значение другого **Variant** . Это то, что другие **Variant** , передаваемый в качестве второго аргумента **OpenSchema**.  
  
 Как Дополнительные примеры, первый аргумент **найти** метод **Variant** , значение которого равно одномерный **SafeArray**каждой необязательных аргументов первого и второго из **AddNew** является одномерным **SafeArray**; и возвращаемое значение **GetRows** метод **Variant** которого значение является двумерным **SafeArray**.  
  
## <a name="missing-and-default-parameters"></a>Отсутствует и параметры по умолчанию,  
 Visual Basic позволяет отсутствуют параметры в методы. Например **записей** объект **откройте** метод имеет пять параметров, но вы можете пропустить промежуточные параметры и не указываете конечные параметры. По умолчанию **BSTR** или **Variant** арабские цифры будут заменены в зависимости от типа данных отсутствует операнд.  
  
 В C/C++ необходимо указать все операнды. Если вы хотите указать отсутствующего параметра, тип данных которого является строкой, укажите **_bstr_t** содержащий строку null. Если вы хотите указать отсутствует параметр, тип данных которого находится **Variant**, укажите **_variant_t** со значением DISP_E_PARAMNOTFOUND и типом значения VT_ERROR. В качестве альтернативы задать эквивалентную **_variant_t** константы, **vtMissing**, который предоставляется свойством **#import** директива.  
  
 Три метода являются исключениями для обычной работы **vtMissing**. Это **Execute** методы **подключения** и **команда** объектов и **NextRecordset** метод **Записей** объекта. Ниже приведены их сигнатуры.  
  
```cpp
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```
  
 Параметры, *RecordsAffected* и *параметры*, являются указателями на **Variant**. *Параметры* является входным параметром, который указывает адрес **Variant** содержит один параметр или массив параметров, определяющие выполняемой команды. *RecordsAffected* является выходным параметром, который указывает адрес **Variant**, где возвращается число строк, затронутых этим методом.  
  
 В **команда** объект **Execute** метода, указать, что параметры не указаны, задав *параметры* либо `&vtMissing` (что рекомендуется) или указатель null (то есть **NULL** или нуль (0)). Если *параметры* устанавливается на указатель null, метод внутренне подставляет эквивалент **vtMissing**и затем завершает операцию.  
  
 Во всех методах указывают, что количество обработанных записей не должно возвращаться, задав *RecordsAffected* пустой указатель. В этом случае пустой указатель не так много отсутствует параметр для указания, что метод должен отменить количество обработанных записей.  
  
 Таким образом для этих трех методов, является допустимым для таких как написать код:  
  
```cpp
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```
  
## <a name="error-handling"></a>Обработка ошибок  
 В модели COM большинство операций возвращает код возврата HRESULT, указывающее, успешно ли завершен функции. **#Import** директива приводит к возникновению ошибки кода программы-оболочки вокруг каждого «raw» метод или свойство и проверяет возвращаемое значение HRESULT. Если значение HRESULT указывает на ошибку, код оболочки выводит ошибку COM, вызывающий _com_issue_errorex() с кодом возврата HRESULT в качестве аргумента. Ошибка COM-объектов может быть перехвачено в **попробуйте**-**catch** блока. (Ради повышения эффективности в catch ссылку **_com_error** объекта.)  
  
 Помните, что ошибки ADO: они возникли: вследствие сбоя операции ADO. Отображаются ошибки, возвращенные базового поставщика как **ошибка** объекты в **подключения** объект **ошибки** коллекции.  
  
 **#Import** директива создает только сообщение об ошибке процедуры обработки для методов и свойств, объявленных в ADO DLL-файл. Тем не менее можно воспользоваться преимуществами такая же ошибка, механизм обработки путем написания собственных ошибка при проверке макросу или встраиваемой функции. См. в разделе [расширений Visual C++](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md), или код в следующих разделах примеры.  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Visual C++, эквивалентные соглашения о Visual Basic  
 Ниже приведен краткий перечень несколько соглашений в документации по ADO, закодированных в Visual Basic, а также их эквиваленты в Visual C++.  
  
### <a name="declaring-an-ado-object"></a>Объявление объекта ADO  
 В Visual Basic, переменная объекта ADO (в данном случае для **записей** объекта) объявляется следующим образом:  
  
```vb
Dim rst As ADODB.Recordset  
```
  
 Предложение "`ADODB.Recordset`«, — это идентификатор ProgID **записей** объекта, как определено в реестре. Новый экземпляр класса **записи** объекта объявляется следующим образом:  
  
```vb
Dim rst As New ADODB.Recordset  
```
  
 -или-  
  
```vb
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```
  
 В Visual C++ **#import** директива вызовет объявления типа смарт-указателя для всех объектов ADO. Например, переменную, которая указывает на **_Recordset** объект имеет тип **_RecordsetPtr**и объявляется следующим образом:  
  
```cpp
_RecordsetPtr  rs;  
```
  
 Переменную, которая указывает на новый экземпляр класса **_Recordset** объект объявляется следующим образом:  
  
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
  
 После **CreateInstance** вызывается метод, переменная может использоваться следующим образом:  
  
```cpp
rs->Open(...);  
```
  
 Обратите внимание, что в одном из случаев "`.`" является оператором так, будто переменной экземпляра класса (`rs.CreateInstance`) и в другом случае "`->`" оператор используется так, будто переменной указатель на интерфейс (`rs->Open`).  
  
 Одну переменную можно использовать двумя способами, так как "`->`" оператор перегружен, чтобы разрешить экземпляра класса ведут себя как указатель на интерфейс. Закрытый класс член переменной экземпляра содержит указатель на **_Recordset** интерфейса; "`->`" оператор возвращает этому указателю; и возвращенный указатель обращается к членами **_Recordset**  объекта.  
  
### <a name="coding-a-missing-parameter---string"></a>Кодирование отсутствует параметр - строка  
 При необходимости код отсутствует **строка** операнда в Visual Basic, просто опускать операнд. Необходимо указать операнд в Visual C++. Код **_bstr_t** , имеющего пустую строку в качестве значения.  
  
```cpp
_bstr_t strMissing(L"");  
```
  
### <a name="coding-a-missing-parameter---variant"></a>Кодирование пропущенного параметра - типа Variant  
 При необходимости код отсутствует **Variant** операнда в Visual Basic, просто опускать операнд. Необходимо указать все операнды в Visual C++. Код отсутствует **Variant** параметр с **_variant_t** специальное значение, DISP_E_PARAMNOTFOUND и тип, VT_ERROR. Можно также задать **vtMissing**, которой эквивалентное Предопределенная константа предоставляемую **#import** директива.  
  
```cpp
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```
  
 \- или -  
  
```cpp
...vtMissing...;  
```
  
### <a name="declaring-a-variant"></a>Объявление типа Variant  
 В Visual Basic **Variant** объявлен с **Dim** следующим образом:  
  
```vb
Dim VariableName As Variant  
```
  
 В визуальном элементе C++, объявите переменную как тип **_variant_t**. Несколько схема **_variant_t** объявления, показаны ниже.  
  
> [!NOTE]
>  Эти объявления просто предоставить примерно представляете себе, что кода в своей программе. Дополнительные сведения см. в приведенных ниже примерах и документации Visual C ++.  
  
```cpp
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```
  
### <a name="using-arrays-of-variants"></a>Использование массивов объектов типа Variant  
 В Visual Basic, массивы **варианты** оформляются с **Dim** инструкции или вы можете использовать **массива** функции, как показано в следующем примере кода:  
  
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
  
 Следующий визуальный C++ примере показано использование метода **SafeArray** использовании **_variant_t**.  
  
#### <a name="notes"></a>Примечания  
 Следующие заметки о соответствуют закомментированные разделы в примере кода.  
  
1.  Опять же чтобы воспользоваться преимуществами существующих механизма обработки ошибок определяется TESTHR() встроенная функция.  
  
2.  Требуется только одномерный массив, поэтому вы можете использовать **SafeArrayCreateVector**, вместо общего назначения **SAFEARRAYBOUND** объявления и **SafeArrayCreate** функция. Ниже приведен код будет выглядеть, как при использовании **SafeArrayCreate**:  
  
    ```cpp
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```
  
3.  Схеме, определенной значением константы перечислимого типа, **adSchemaColumns**, связанный с четырьмя столбцами ограничение: Значениям TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME и COLUMN_NAME. Таким образом, массив **Variant** создается значений с четырьмя элементами. Затем указывается значение ограничения, которое соответствует с третьим столбцом, TABLE_NAME.  
  
     **Записей** возвращаемый состоит из нескольких столбцов, подмножество из которых представляет столбцы с ограничением. Значения столбцов ограничения для каждой возвращаемой строке должен быть таким же, как соответствующие значения ограничения.  
  
4.  Если вы знакомы с **объекты SAFEARRAY** может быть удивлены, **SafeArrayDestroy**() не вызывается до завершения работы. На самом деле, вызвав **SafeArrayDestroy**() в этом случае будет вызвать исключение времени выполнения. Причина в том, что деструктор для `vtCriteria` вызовет **VariantClear**() при **_variant_t** выходит за пределы области, который, чтобы освободить **SafeArray**. Вызов **SafeArrayDestroy**, без очистки вручную **_variant_t**, вызовет деструктор, чтобы попытаться очистить при использовании недопустимого **SafeArray** указатель.  
  
     Если **SafeArrayDestroy** были вызывается, код будет выглядеть следующим образом:  
  
    ```cpp
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```
  
     Тем не менее, гораздо проще разрешить **_variant_t** управление **SafeArray**.  
  
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
  
### <a name="using-property-getputputref"></a>С помощью свойства Get/Put/PutRef  
 В Visual Basic имя свойства не уточняется ли его получить, назначенный или присвоить ссылку.  
  
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
  
 В этом примере Visual C++ показано **получить**/**поместить**/**PutRef**_свойство_.  
  
#### <a name="notes"></a>Примечания  
 Следующие заметки о соответствуют закомментированные разделы в примере кода.  
  
1.  В этом примере используется два вида пропущен строковый аргумент: константу явные **strMissing**и строку, компилятор будет использовать для создания временной **_bstr_t** , будет существовать в рамках  **Откройте** метод.  
  
2.  Нет необходимости для приведения операнда `rs->PutRefActiveConnection(cn)` для `(IDispatch *)` так как тип операнда уже `(IDispatch *)`.  
  
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
  
### <a name="using-getitemx-and-itemx"></a>С помощью GetItem(x) и элемент [x]  
 Этот пример Visual Basic демонстрируется синтаксис стандартного и альтернативного **элемент**().  
  
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
  
 В этом примере Visual C++ показано **элемент**.  
  
> [!NOTE]
>  Следующее примечание соответствует комментариями разделы в примере кода:  При обращении к коллекции с **элемент**, индекс, **2**, должен быть приведен к **long** , вызывается соответствующий конструктор.  
  
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
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>Приведение указателей объектов ADO с (IDispatch *)  
 В следующем примере Visual C++ демонстрируется использование (IDispatch *) для указателей объектов ADO приведения.  
  
#### <a name="notes"></a>Примечания  
 Следующие заметки о соответствуют закомментированные разделы в примере кода.  
  
1.  Укажите открытый **подключения** объекта в явно закодированных **Variant**. Приведите его с (IDispatch \*) Поэтому надлежащий конструктор будет вызываться. Кроме того, явно задать второй **_variant_t** параметр значение по умолчанию **true**, поэтому счетчик ссылок объекта будут правильными при **Recordset::Open** Завершает операцию.  
  
2.  Выражение, `(_bstr_t)`, не приведения к типу, но **_variant_t** оператор, который извлекает **_bstr_t** строка из **Variant** возвращаемые **значение** .  
  
 Выражение, `(char*)`, не приведения к типу, но **_bstr_t** оператор, который извлекает указатель на строку, инкапсулированный в **_bstr_t** объекта.  
  
 Этот раздел кода показаны некоторые полезные поведения **_variant_t** и **_bstr_t** операторы.  
  
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

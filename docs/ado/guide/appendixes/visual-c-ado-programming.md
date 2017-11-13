---
title: "ADO программирования Visual C++ | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO]
ms.assetid: 11233b96-e05c-4221-9aed-5f20944b0f1c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9000f90f30c8761845305e75cf3d0ea7ea86927a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="visual-c-ado-programming"></a>ADO программирования Visual C++
Справочник по API ADO Описывает функциональные возможности ADO интерфейс программирования (API) с помощью синтаксиса для Microsoft Visual Basic. То, что целевая аудитория всем пользователям, программистам ADO используют разных языков, например Visual Basic, Visual C++ (с и без **#import** директивы) и Visual J ++ (с пакетом класс ADO/WFC).  

> [!NOTE]
> Поддержка Microsoft завершен для Visual J ++ в 2004 году.

 Для размещения этого разнообразия [ADO для Visual C++ синтаксис индексов](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) предоставляют синтаксис конкретного языка Visual C++ со ссылками на общие описания функциональности, параметров, исключительные поведения и т. д., в API Ссылка.  
  
 ADO реализуется с помощью интерфейсов COM (компонент объектной модели). Однако проще программистам работать с COM в некоторых языках программирования, чем другие. Например почти все сведения об использовании COM обрабатываются неявно для программистов Visual Basic, в то время как для программистов Visual C++ необходимо обращать внимание на эти сведения сами.  
  
 В следующих разделах приведены сведения для программистов C и C++, с помощью ADO и **#import** директивы. Этот раздел посвящен типы данных, относящиеся к COM (**Variant**, **BSTR**, и **SafeArray**) и обработка ошибок (_com_error).  
  
## <a name="using-the-import-compiler-directive"></a>С помощью компилятора директивы #import  
 **#Import** директивы компилятора Visual C++ упрощает работу с ADO методы и свойства. Директива принимает имя файла, содержащего библиотеку типов, таких как ADO DLL-файл (Msado15.dll) и создает файлы заголовков, содержащие объявления typedef, интеллектуальных указателей для интерфейсов, а констант-перечислителей. Каждый интерфейс инкапсулированный или в оболочку, в классе.  
  
 Для каждой операции в пределах класса (то есть вызов метода или свойства) нет объявления для вызова операции непосредственно (то есть «raw» форма операции) и объявления, чтобы вызвать операцию необработанные и выдавать ошибку COM, если операцию не удается выполнить succ essfully. Если операция является свойством, нет обычно директивы компилятора, который создает альтернативный синтаксис для операции, которая имеет синтаксис, такой как Visual Basic.  
  
 Операции, которые извлечь значение свойства имеют имена в формате **получить***свойства*. Операций, которые задают значение свойства имеют имена в формате **поместить***свойства*. Операций, которые задают значение свойства с помощью указателя на объект ADO имеют имена в формате **PutRef***свойства*.  
  
 Можно получить или задать свойство с вызовами следующие формы:  
  
```  
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```  
  
## <a name="using-property-directives"></a>Свойство директив using  
 **__Declspec(property...)**  директиву компилятора — это расширение языка C для систем Microsoft, который объявляет функцию, которая используется как свойство иметь альтернативный синтаксис. В результате можно задать или получить значения свойства таким образом, аналогично Visual Basic. Например можно задать и получить свойство таким образом:  
  
```  
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```  
  
 Обратите внимание, что у вас в код:  
  
```  
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```  
  
 Компилятор создает соответствующий **получить***-*, **поместить**-, или **PutRef***свойство* вызов на основе какие альтернативный синтаксис объявления и выполняется ли свойство чтения или записи.  
  
 **__Declspec(property...)**  директивы компилятора можно объявлять только **получить**, **поместить**, или **получить** и **поместить** альтернативный синтаксис для функции. Достаточно только операции чтения **получить** объявления; только для записи операции достаточно **поместить** объявления; операции, которые как чтение и запись, иметь оба **получить** и **поместить** объявления.  
  
 С помощью этой директивы; возможны только два объявления Тем не менее, каждое свойство может иметь три свойства функции: **получить***свойство*, **поместить***свойство*, и **PutRef**  *Свойства*. В этом случае только две формы свойства имеют альтернативный синтаксис.  
  
 Например **команда** объекта **ActiveConnection** свойство объявлено с альтернативный синтаксис **получить***ActiveConnection*и **PutRef***ActiveConnection*. **PutRef**-синтаксис будет хорошим выбором, так как на практике обычно требуется поместить открытый **подключения** объект (то есть **подключения** указатель на объект) в этом свойство. С другой стороны **записей** объект имеет **получить**-, **поместить**-, и **PutRef***ActiveConnection*операций, но не альтернативный синтаксис.  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>Коллекции, метод GetItem и свойства элемента  
 ADO определяет несколько коллекций, в том числе **поля**, **параметры**, **свойства**, и **ошибки**. В Visual C++ **GetItem (***индекс***)** метод возвращает элемент из коллекции. *Индекс* — **Variant**, значение которого является числовой индекс элемента в коллекции, или строка, содержащая имя элемента.  
  
 **__Declspec(property...)**  объявляет директиву компилятора **элемент** свойство как альтернативный синтаксис для каждой коллекции фундаментальные **GetItem() для удаленного элемента** метод. Альтернативный синтаксис использует квадратные скобки и выглядит аналогично ссылки на массив. В общем случае две формы выглядеть следующим образом:  
  
```  
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```  
  
 Например, присвоить значение полю из **записей** объекта, с именем ***rs***, который является производным от **авторов** таблицу **pubs** базы данных. Используйте **Item()** свойство для доступа к третьему **поле** из **записей** объекта **поля** коллекции (коллекций индексируются, начиная с равно нулю; Предположим, третье поле называется ***Фамилия_автора***). Затем вызовите **Value()** метод **поле** объекта для присвоения значения строки.  
  
 Это может быть задано в Visual Basic следующими четырьмя способами (последние две формы являются уникальными для Visual Basic) не имеют эквивалентов в других языках:  
  
```  
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```  
  
 Является эквивалентом в Visual C++ для первых двух форм выше:  
  
```  
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```  
  
 - или - (альтернативный синтаксис **значение** свойства также отображается)  
  
```  
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```  
  
 Примеры итерации по коллекции см. раздел «Коллекции ADO» «Справочник по ADO».  
  
## <a name="com-specific-data-types"></a>Типы данных COM  
 Как правило любой тип данных Visual Basic, которые можно найти в справочнике по API-Интерфейс ADO имеет эквивалентом Visual C++. К ним относятся стандартные типы данных, такие как **unsigned char** для Visual Basic **байтов**, **короткие** для **целое число со знаком**, и  **длинное** для **длинные**. Поиск в Indexesto синтаксиса см. именно то, что необходимо для операндов данного метода или свойства.  
  
 Исключением из этого правила являются типами данных, относящиеся к COM: **Variant**, **BSTR**, и **SafeArray**.  
  
### <a name="variant"></a>Variant  
 Объект **Variant** — тип структурированных данных, который содержит значение и тип данных элемента. Объект **Variant** может содержать широкий набор типов данных, включая другой вариант, BSTR, логическое значение, IDispatch или IUnknown указатель, валюты, даты и т. д. COM также предоставляет методы, которые позволяют легко преобразовать данные из одного типа в другой.  
  
 **_Variant_t** класс инкапсулирует и управляет **Variant** тип данных.  
  
 Справочник по API ADO говорит метод или свойство операнд имеет значение, это обычно означает значение, переданное в **_variant_t**.  
  
 Это правило явно значение true, если **параметры** раздел в разделах справочника API-Интерфейс ADO говорит операнд **Variant**. Единственное исключение — когда документации явно говорит операнд принимает стандартным типом данных, таких как **длинные** или **байтов**, или перечисления. Еще одно исключение — когда принимает операнд **строка**.  
  
### <a name="bstr"></a>BSTR  
 Объект **BSTR** (**B**вентиляторами **STR**ing) — это тип структурированных данных, содержащий строку символов и длину строки. COM предоставляет методы для выделения, управлять и без **BSTR**.  
  
 **_Bstr_t** класс инкапсулирует и управляет **BSTR** тип данных.  
  
 При ошибке Справочник по API ADO метод или свойство принимает **строка** значение, это означает, значение в виде **_bstr_t**.  
  
### <a name="casting-variantt-and-bstrt-classes"></a>Приведение классы _variant_t и _bstr_t  
 Обычно нет необходимости явно кода **_variant_t** или **_bstr_t** в аргументе операции. Если **_variant_t** или **_bstr_t** класс имеет конструктор, который совпадает с типом данных аргумента, компилятор создает соответствующий **_variant_t** или **_bstr_t**.  
  
 Тем не менее если аргумент является неоднозначным, то есть тип данных аргумента соответствует более одного конструктора, необходимо привести аргумент с типом данных, соответствующий вызов надлежащего конструктора.  
  
 Например, объявление для **Recordset::Open** является метод:  
  
```  
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```  
  
 `ActiveConnection` Аргумент принимает ссылку на **_variant_t**, которого может быть написан как строка подключения или указатель на открытый **подключения** объекта.  
  
 Правильные **_variant_t** будет создан неявно при передаче строки, такие как «`DSN=pubs;uid=MyUserName;pwd=MyPassword;`», или указателя, такие как «`(IDispatch *) pConn`».  
  
> [!NOTE]
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.  
  
 Или может явно создавать код **_variant_t** содержащий указателя, такие как «`_variant_t((IDispatch *) pConn, true)`». Приведение, `(IDispatch *)`, устраняет неоднозначность с другой конструктор, который принимает указатель на интерфейс IUnknown.  
  
 Очень важно, хотя редко упомянутые факт, что ADO интерфейс IDispatch. Каждый раз, когда указатель на объект ADO должны передаваться как **Variant**, что указатель должен быть приведен как указатель на интерфейс IDispatch.  
  
 Последний вариант явно коды второй логический аргумент конструктора с необязательным, значение по умолчанию `true`. Этот аргумент указывает **Variant** конструктор вызывать его **AddRef**() метода, который компенсирует ADO автоматический вызов **_variant_t::Release**метод) После завершения вызова метода или свойства ADO.  
  
### <a name="safearray"></a>SafeArray  
 Объект **SafeArray** — тип структурированных данных, который содержит массив типов данных. Объект **SafeArray** называется *безопасном* , так как он содержит сведения о границах каждого измерения массива и ограничивает доступ к элементам массива в пределах этих границ.  
  
 Когда Справочник по API ADO говорит метод или свойство принимает или возвращает массив, значит метод или свойство принимает или возвращает **SafeArray**, не собственный массив C/C++.  
  
 Например, второй параметр **подключения** объекта **OpenSchema** методу требуется массив **Variant** значения. Те **Variant** значения должны передаваться как элементы **SafeArray**и что **SafeArray** должен быть задан как значение другого **Variant** . Это то, что другие **Variant** , передаваемого в качестве второго аргумента **OpenSchema**.  
  
 Примеры как более подробно, первый аргумент **найти** метод **Variant** , значение которого представляет одномерный **SafeArray**каждой необязательных аргументов первого и второго из **AddNew** является одномерного **SafeArray**; и значение, возвращаемое **GetRows** метод **Variant** которого значение является двумерным **SafeArray**.  
  
## <a name="missing-and-default-parameters"></a>Отсутствует и параметры по умолчанию  
 Visual Basic позволяет отсутствует параметрам в методах. Например **записей** объекта **откройте** метод имеет пять параметров, но можно пропустить промежуточные параметры и не ставятся конечные параметры. Значение по умолчанию **BSTR** или **Variant** будут заменены в зависимости от типа данных отсутствует операнд.  
  
 В C/C++ необходимо указать все операнды. Если вы хотите указать отсутствует параметр, тип данных которого является строкой, укажите **_bstr_t** содержащую пустой строкой. Если вы хотите указать отсутствует параметр, тип данных которого является **Variant**, укажите **_variant_t** со значением DISP_E_PARAMNOTFOUND и тип VT_ERROR. Можно также указать эквивалент **_variant_t** константой, **vtMissing**, который предоставляется с **#import** директивы.  
  
 Три метода не распространяется на типовое использование объекта **vtMissing**. Это **Execute** методы **подключения** и **команда** объектов и **NextRecordset** метод **Записей** объекта. Ниже приведены их сигнатуры.  
  
```  
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```  
  
 Параметры, *RecordsAffected* и *параметры*, являются указателями на **Variant**. *Параметры* является входным параметром, который указывает адрес **Variant** содержит один параметр или массив параметров, изменяющих выполняемой команды. *RecordsAffected* является выходным параметром, который указывает адрес **Variant**, где возвращается число строк, затронутых методом.  
  
 В **команда** объекта **Execute** метода, указывает, что параметры не указаны, задав *параметры* либо `&vtMissing` (что рекомендуется) или указатель null (то есть **NULL** или ноль (0)). Если *параметры* устанавливается на указатель null, метод внутренне замещает эквивалент **vtMissing**и завершает операцию.  
  
 Во всех методах, указывают, что количество обработанных записей не должна возвращаться, задав *RecordsAffected* на указатель null. В этом случае пустой указатель не так много отсутствует параметр что указывает на то, что метод должен отменить количество обработанных записей.  
  
 Таким образом для следующих трех методов, является допустимым написать код таких как:  
  
```  
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```  
  
## <a name="error-handling"></a>Обработка ошибок  
 В COM большинство операций возвращают код возврата HRESULT, указывающее, успешно ли выполнено функции. **#Import** директивы приводит к возникновению ошибки кода программы-оболочки вокруг каждого «raw» метод или свойство и проверяет, возвращенное значение HRESULT. Если значение HRESULT указывает на сбой, код программы-оболочки вызывает COM-ошибки путем вызова _com_issue_errorex() с кодом возврата HRESULT в качестве аргумента. Ошибка COM-объектов может быть перехвачена в **повторите**-**перехватывать** блока. (Ради повышения его эффективности перехватывать ссылку на **_com_error** объекта.)  
  
 Помните, что они являются ошибками ADO: они являются результатом сбоя операции ADO. Базовый поставщик вернул ошибки отображаются в виде **ошибка** объекты в **подключения** объекта **ошибки** коллекции.  
  
 **#Import** директива создает только сообщение об ошибке подпрограммы обработки для методов и свойств, объявленных в ADO DLL-файл. Тем не менее можно воспользоваться преимуществами этой же ошибка, механизм обработки, написав собственные проверки макросу или встроенной функции ошибок. См. в разделе [расширения Visual C++](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md), или код в следующих разделах примеры.  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Эквиваленты Visual C++, Visual Basic соглашений  
 Ниже приведен перечень несколько соглашений в документации по ADO, закодированных в Visual Basic, а также их эквиваленты в Visual C++.  
  
### <a name="declaring-an-ado-object"></a>Объявление объекта ADO  
 В Visual Basic, переменная объекта ADO (в данном случае для **записей** объекта) объявляется следующим образом:  
  
```  
Dim rst As ADODB.Recordset  
```  
  
 Предложение "`ADODB.Recordset`», имеет идентификатор ProgID **записей** объекта, как определено в реестре. Новый экземпляр **записи** объект объявляется следующим образом:  
  
```  
Dim rst As New ADODB.Recordset  
```  
  
 -или-  
  
```  
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```  
  
 В Visual C++ **#import** директива создает смарт-указателю объявления для всех объектов ADO. Например, переменная, которая указывает **_Recordset** объект имеет тип **_RecordsetPtr**и объявляется следующим образом:  
  
```  
_RecordsetPtr  rs;  
```  
  
 Переменная, которая указывает новый экземпляр **_Recordset** объект объявляется следующим образом:  
  
```  
_RecordsetPtr  rs("ADODB.Recordset");  
```  
  
 -или-  
  
```  
_RecordsetPtr  rs;  
rs.CreateInstance("ADODB.Recordset");  
```  
  
 -или-  
  
```  
_RecordsetPtr  rs;  
rs.CreateInstance(__uuidof(_Recordset));  
```  
  
 После **CreateInstance** вызывается метод, переменная может использоваться следующим образом:  
  
```  
rs->Open(...);  
```  
  
 Обратите внимание, что в первом случае "`.`" оператор используется как бы переменная экземпляра класса (`rs.CreateInstance`) и в другом случае "`->`" оператор используется, как будто переменной указателя на интерфейс (`rs->Open`).  
  
 На одну переменную можно использовать двумя способами, так как "`->`" оператор перегружен, чтобы разрешить экземпляр класса вел себя как указатель на интерфейс. Закрытый класс член переменной экземпляра содержит указатель на **_Recordset** интерфейса; "`->`«оператор возвращает данный указатель; и возвращаемого указателя обращается к члены **_Recordset**  объекта.  
  
### <a name="coding-a-missing-parameter--string"></a>Отсутствует параметр кодирования — строка  
 При необходимости код отсутствующего **строка** операнд в Visual Basic просто опускать операнд. В Visual C++, необходимо указать значение операнда. Код **_bstr_t** , содержащее пустую строку как значение.  
  
```  
_bstr_t strMissing(L"");  
```  
  
### <a name="coding-a-missing-parameter--variant"></a>Отсутствует параметр кодирования — Variant  
 При необходимости код отсутствующего **Variant** операнд в Visual Basic просто опускать операнд. Необходимо указать все операнды в Visual C++. Код отсутствующего **Variant** параметр с **_variant_t** специальное значение, DISP_E_PARAMNOTFOUND и тип VT_ERROR. Можно также указать **vtMissing**, которой эквивалентные Предопределенная константа предоставляемую **#import** директивы.  
  
```  
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```  
  
 - или -  
  
```  
...vtMissing...;  
```  
  
### <a name="declaring-a-variant"></a>Объявление типа Variant  
 В Visual Basic **Variant** объявлен с **Dim** следующим образом:  
  
```  
Dim VariableName As Variant  
```  
  
 В Visual C++, объявите переменную как тип **_variant_t**. Схематическое изображение несколько **_variant_t** объявления показаны ниже.  
  
> [!NOTE]
>  Эти объявления просто присвойте грубое представление образом коду в собственную программу. Дополнительные сведения см. в приведенных ниже примерах и документации Visual С ++.  
  
```  
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```  
  
### <a name="using-arrays-of-variants"></a>Использование массивов типа Variant  
 В Visual Basic, массивы **варианты** могут разрабатываться с **Dim** инструкции, или же может использовать **массива** функции, как показано в следующем примере кода:  
  
```  
Public Sub ArrayOfVariants  
Dim cn As ADODB.Connection  
Dim rs As ADODB.Recordset  
Dim fld As ADODB.Field  
  
    cn.Open "DSN=pubs"  
    rs = cn.OpenSchema(adSchemaColumns, _  
        Array(Empty, Empty, "authors", Empty))  
    For Each fld in rs.Fields  
        Debug.Print "Name = "; fld.Name  
    Next fld  
    rs.Close  
    cn.Close  
End Sub  
```  
  
 В следующем примере Visual C++ демонстрируется использование **SafeArray** с **_variant_t**.  
  
#### <a name="notes"></a>Примечания  
 Следующие примечания соответствуют закомментированный разделы в примере кода.  
  
1.  Опять же чтобы воспользоваться преимуществами существующего механизма обработки ошибок определяется TESTHR() встроенной функции.  
  
2.  Требуется только одномерный массив, чтобы можно было использовать **SafeArrayCreateVector**, вместо общего назначения **SAFEARRAYBOUND** объявления и **SafeArrayCreate** функция. Ниже приведен код будет выглядеть подобно использованию **SafeArrayCreate**:  
  
    ```  
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```  
  
3.  Схемы, обозначенную Перечислимая константа **adSchemaColumns**, связанный с четырьмя столбцами ограничение: значениям TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME и COLUMN_NAME. Таким образом, массив **Variant** создается значений с четырьмя элементами. Затем задается значение ограничения, которое соответствует третьим столбцом, TABLE_NAME.  
  
     **Записей** возвращаемый состоит из нескольких столбцов, подмножество из которых представляет столбцы с ограничением. Значения столбцов ограничения для каждой возвращаемой строке должен совпадать с соответствующими значениями ограничений.  
  
4.  Если вы знакомы с **массивов SafeArray** может быть удивлены, **SafeArrayDestroy**() не вызывается до завершения. Фактически, вызов **SafeArrayDestroy**() в этом случае будет вызвать исключение времени выполнения. Это вызвано тем, деструктор для `vtCriteria` вызовет **VariantClear**() при **_variant_t** выходит за пределы области, которая освободить **SafeArray**. Вызов **SafeArrayDestroy**, без очистки вручную **_variant_t**, приведет к тому, деструктор, чтобы попытаться очистить недопустимое **SafeArray** указателя.  
  
     Если **SafeArrayDestroy** был вызван, код будет выглядеть следующим образом:  
  
    ```  
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```  
  
     Однако это гораздо проще позволить **_variant_t** управления **SafeArray**.  
  
```  
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
  
### <a name="using-property-getputputref"></a>С помощью свойства Get и Put/PutRef  
 В Visual Basic имя свойства не квалифицируется ли его получить, назначенный или назначить ссылку.  
  
```  
Public Sub GetPutPutRef  
Dim rs As New ADODB.Recordset  
Dim cn As New ADODB.Connection  
Dim sz as Integer  
cn.Open "Provider=sqloledb;Data Source=yourserver;" & _  
         "Initial Catalog=pubs;Integrated Security=SSPI;"  
rs.PageSize = 10  
sz = rs.PageSize  
rs.ActiveConnection = cn  
rs.Open "authors",,adOpenStatic  
' ...  
rs.Close  
cn.Close  
End Sub  
```  
  
 В этом примере Visual C++ демонстрируется **получить**/**поместить**/**PutRef***свойства*.  
  
#### <a name="notes"></a>Примечания  
 Следующие примечания соответствуют закомментированный разделы в примере кода.  
  
1.  В этом примере используется два вида пропущен строковый аргумент: явное константа **strMissing**и строка, компилятор будет использовать для создания временной **_bstr_t** , будет находиться в пределах области  **Откройте** метод.  
  
2.  Необязательно для приведения операнда `rs->PutRefActiveConnection(cn)` для `(IDispatch *)` так как тип операнда уже `(IDispatch *)`.  
  
```  
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
  
### <a name="using-getitemx-and-itemx"></a>С помощью GetItem(x) и элемента [x]  
 В этом примере Visual Basic демонстрируется синтаксис стандартного и альтернативного **элемент**().  
  
```  
Public Sub GetItemItem  
Dim rs As New ADODB.Recordset  
Dim name as String  
rs = rs.Open "authors", "DSN=pubs;", adOpenDynamic, _  
         adLockBatchOptimistic, adTable  
name = rs(0)  
' -or-  
name = rs.Fields.Item(0)  
rs(0) = "Test"  
rs.UpdateBatch  
' Restore name  
rs(0) = name  
rs.UpdateBatch  
rs.Close  
End Sub  
```  
  
 В этом примере Visual C++ демонстрируется **элемент**.  
  
> [!NOTE]
>  Следующее примечание соответствует закомментированный разделы в примере кода: при обращении к коллекции с **элемент**, индекс, **2**, должен быть приведен к **длинные** , вызывается соответствующий конструктор.  
  
```  
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
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>Приведение указателей на объекты ADO с (IDispatch *)  
 В следующем примере Visual C++ демонстрируется использование (IDispatch *) для приведения указателей на объекты ADO.  
  
#### <a name="notes"></a>Примечания  
 Следующие примечания соответствуют закомментированный разделы в примере кода.  
  
1.  Укажите открытый **подключения** объекта в явном виде закодированного **Variant**. С помощью приведения (IDispatch \*), надлежащий конструктор будет вызываться. Кроме того, явно установите второй **_variant_t** параметр в значение по умолчанию **true**, поэтому счетчик ссылок объекта будут правильными при **Recordset::Open** операция завершается.  
  
2.  Выражение, `(_bstr_t)`, не является приведения к типу, но **_variant_t** оператор, который извлекает **_bstr_t** строка, в **Variant** возвращенных **значение** .  
  
 Выражение, `(char*)`, не приведения, но **_bstr_t** оператор, который извлекает указатель на строку, инкапсулированный в **_bstr_t** объекта.  
  
 Этот раздел кода демонстрируются некоторые полезные расширений функциональности **_variant_t** и **_bstr_t** операторы.  
  
```  
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


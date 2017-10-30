---
title: "Основные сведения о модели объектов компонента скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 09de00344fe94087b6287b07c4b1ffe933d27b7c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="understanding-the-script-component-object-model"></a>Основные сведения о модели объектов компонента скрипта
  Как было сказано в [кодировании и отладке компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md), проект компонента скрипта содержит три элемента проекта:  
  
1.  **ScriptMain** элемент, который содержит **ScriptMain** класса, в котором создается код. **ScriptMain** класс наследует от **UserComponent** класса.  
  
2.  **ComponentWrapper** элемент, который содержит **UserComponent** класса, экземпляр <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> , содержащий методы и свойства, которые будут использоваться для обработки данных и взаимодействия с пакетом. **ComponentWrapper** содержит также **подключений** и **переменных** классы коллекций.  
  
3.  **BufferWrapper** элемент, который содержит классы, унаследованные от <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> для каждого входного и выходного и типизированные свойства для каждого столбца.  
  
 При написании кода в **ScriptMain** элемент, будет использовать объекты, методы и свойства, рассматриваемые в этом разделе. Компонент может использовать не все перечисленные здесь методы. Однако если они используются, то используются в указанной последовательности.  
  
 Базовый класс <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> не содержит кода, реализующего методы, которые обсуждаются в данном разделе. Поэтому вызов базового класса в вашей собственной реализации этого метода не обязателен, но безопасен.  
  
 Сведения о том, как использовать методы и свойства этих классов в компоненте скрипта определенного типа, обратитесь к разделу [Дополнительные примеры компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). В разделах примеров также приведен полный образец кода.  
  
## <a name="acquireconnections-method"></a>Метод AcquireConnections  
 Источники и назначения обычно должны быть соединены с внешним источником данных. Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, чтобы получить соединение или сведения о соединении из соответствующего диспетчера соединений.  
  
 В следующем примере возвращается **System.Data.SqlClient.SqlConnection** из диспетчера соединений ADO.NET.  
  
```vb  
Dim connMgr As IDTSConnectionManager100  
Dim sqlConn As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    connMgr = Me.Connections.MyADONETConnection  
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
End Sub  
```  
  
 Следующий пример возвращает полный путь и имя файла из Flat File Connection Manager и затем открывает файл с помощью **System.IO.StreamReader**.  
  
```vb  
Private textReader As StreamReader  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    Dim connMgr As IDTSConnectionManager100 = _  
        Me.Connections.MyFlatFileSrcConnectionManager  
    Dim exportedAddressFile As String = _  
        CType(connMgr.AcquireConnection(Nothing), String)  
    textReader = New StreamReader(exportedAddressFile)  
  
End Sub  
```  
  
## <a name="preexecute-method"></a>Метод PreExecute  
 Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, если необходимо однократно выполнить некоторые действия перед началом обработки строк данных. Например, в назначении может потребоваться настроить параметризованную команду, которая будет использоваться назначением для вставки строк данных в источник данных.  
  
```vb  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
...  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
```  
  
```csharp  
SqlConnection sqlConn;   
SqlCommand sqlCmd;   
SqlParameter sqlParam;   
  
public override void PreExecute()   
{   
  
    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn);   
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int);   
    sqlCmd.Parameters.Add(sqlParam);   
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);   
    sqlCmd.Parameters.Add(sqlParam);   
  
}  
```  
  
## <a name="processing-inputs-and-outputs"></a>Обработка входов и выходов  
  
### <a name="processing-inputs"></a>Обработка входов  
 Компоненты скрипта, настроенные как преобразования или назначения, имеют один вход.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Содержимое элемента проекта BufferWrapper  
 Для каждой входной настроенного, **BufferWrapper** элемент проекта содержит класс, производный от <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> и имеет то же имя в качестве входных данных. Каждый класс входного буфера содержит перечисленные далее свойства, функции и методы.  
  
-   Именованные и типизированные свойства метода доступа для каждого выбранного входного столбца. Эти свойства доступны только для чтения или чтения и записи, в зависимости от **тип использования** указанный для столбца **входные столбцы** страница **редактор преобразования «скрипт»**.  
  
-   Объект  **\<столбца > _IsNull** свойство для каждого выбранного входного столбца. Это свойство также доступно только для чтения или чтения и записи, в зависимости от **тип использования** указано для столбца.  
  
-   Объект **DirectRowTo\<outputbuffer >** метод для каждого настроенного выхода. Эти методы будет использоваться при фильтрации строк в один или несколько выходов в одной **ExclusionGroup**.  
  
-   Объект **NextRow** функцию для получения следующей входной строки и **EndOfRowset** функцию, чтобы определить, был ли обработан последний буфер данных. Обычно не требуется эти функции при использовании методов, реализованных в обработки ввода **UserComponent** базового класса. В следующем разделе приведены дополнительные сведения о **UserComponent** базового класса.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Содержимое элемента проекта ComponentWrapper  
 Элемент проекта ComponentWrapper содержит класс с именем **UserComponent** , производный от <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. **ScriptMain** класс, в котором создается пользовательский код в свою очередь является производным от **UserComponent**. **UserComponent** класс содержит следующие методы:  
  
-   Переопределенная реализация метода **ProcessInput** метод. Этот метод называется методом данных вызывается подсистемой обработки потока рядом во время выполнения после **PreExecute** метод, который может быть вызван несколько раз. **Метод ProcessInput** передает обработку  **\<inputbuffer > _ProcessInput** метод. Затем **ProcessInput** метод проверяет конец входного буфера и, если был достигнут конец буфера вызывает переопределяемый **FinishOutputs** метод и закрытый **MarkOutputsAsFinished** метод. **MarkOutputsAsFinished** затем вызывает метод **SetEndOfRowset** для последнего выходного буфера.  
  
-   Перегружаемую реализацию  **\<inputbuffer > _ProcessInput** метод. Данная реализация по умолчанию просто последовательно просматривает Входящие строки и вызовы  **\<inputbuffer > _ProcessInputRow**.  
  
-   Перегружаемую реализацию  **\<inputbuffer > _ProcessInputRow** метод. Реализация по умолчанию пуста. Этот метод обычно переопределяется, чтобы написать пользовательский код обработки данных.  
  
#### <a name="what-your-custom-code-should-do"></a>Задачи, выполняемые в пользовательском коде  
 Можно использовать следующие методы для обработки входа в **ScriptMain** класса:  
  
-   Переопределить  **\<inputbuffer > _ProcessInputRow** для обработки данных в каждую входную строку, проходящую через.  
  
-   Переопределить  **\<inputbuffer > _ProcessInput** только в том случае, если необходимо выполнять дополнительные действия при циклической обработке входных строк. (Например, необходимо проверить для **EndOfRowset** вступили в другие действия после того как все строки будут обработаны.) Вызовите  **\<inputbuffer > _ProcessInputRow** для выполнения обработки строк.  
  
-   Переопределить **FinishOutputs** при наличии каким-либо образом выходные данные, прежде чем будут закрыты.  
  
 **ProcessInput** метод гарантирует, что эти методы вызываются в нужное время.  
  
### <a name="processing-outputs"></a>Обработка выходов  
 Компоненты скрипта, настроенные в качестве источников или преобразований, имеют один или несколько выходов.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Содержимое элемента проекта BufferWrapper  
 Для каждого настроенного выхода элемент проекта BufferWrapper содержит класс, порожденный от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> и совпадающий по имени с выходом. Каждый класс входного буфера содержит перечисленные далее свойства и методы.  
  
-   Именованные и типизированные свойства метода доступа только для записи для каждого выходного столбца.  
  
-   Только для записи  **\<столбца > _IsNull** свойство для каждого выбранного выходного столбца, который можно использовать для задания значения столбца **null**.  
  
-   **Метода AddRow** метод, чтобы добавить новую пустую строку в выходной буфер.  
  
-   Объект **SetEndOfRowset** метод, чтобы знать, что больше нет буферов данных должны подсистема обработки потока данных. Имеется также **EndOfRowset** функции, чтобы определить, является ли текущий буфер последний буфер данных. Обычно нет необходимости эти функции при использовании методов, реализованных в обработки ввода **UserComponent** базового класса.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Содержимое элемента проекта ComponentWrapper  
 Элемент проекта ComponentWrapper содержит класс с именем **UserComponent** , производный от <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. **ScriptMain** класс, в котором создается пользовательский код в свою очередь является производным от **UserComponent**. **UserComponent** класс содержит следующие методы:  
  
-   Переопределенная реализация метода **PrimeOutput** метод. Подсистема обработки потока данных вызывает этот метод перед **ProcessInput** во время выполнения, и он вызывается только один раз. **Метод PrimeOutput** передает обработку **CreateNewOutputRows** метод. Затем, если компонент является источником (то есть компонент имеет нет входных данных), **PrimeOutput** вызывает переопределяемый **FinishOutputs** метод и закрытый **MarkOutputsAsFinished** метод. **MarkOutputsAsFinished** вызовы метода **SetEndOfRowset** для последнего выходного буфера.  
  
-   Перегружаемую реализацию **CreateNewOutputRows** метод. Реализация по умолчанию пуста. Этот метод обычно переопределяется, чтобы написать пользовательский код обработки данных.  
  
#### <a name="what-your-custom-code-should-do"></a>Задачи, выполняемые в пользовательском коде  
 Можно использовать следующие методы для обработки выходов в **ScriptMain** класса:  
  
-   Переопределить **CreateNewOutputRows** только когда Добавление и заполнение выходных строк перед обработкой входных строк. Например, можно использовать **CreateNewOutputRows** в источнике, но в преобразования с асинхронными выходами, необходимо вызвать **метода AddRow** во время или после обработки входных данных.  
  
-   Переопределить **FinishOutputs** при наличии каким-либо образом выходные данные, прежде чем будут закрыты.  
  
 **PrimeOutput** метод гарантирует, что эти методы вызываются в нужное время.  
  
## <a name="postexecute-method"></a>Метод PostExecute  
 Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, если необходимо однократно выполнить некоторые действия после обработки всех строк данных. Например, в источнике, может потребоваться закрыть окно **System.Data.SqlClient.SqlDataReader** вы использовали для загрузки данных в потоке данных.  
  
> [!IMPORTANT]  
>  Коллекция **ReadWriteVariables** доступна только в **PostExecute** метод. Поэтому нельзя непосредственно увеличивать значение переменной пакета после обработки каждой строки данных. Вместо этого увеличьте значение локальной переменной и значение переменной пакета значение локальной переменной в **PostExecute** метод после все данные были обработаны.  
  
## <a name="releaseconnections-method"></a>Метод ReleaseConnections  
 Источники и назначения обычно должны быть соединены с внешним источником данных. Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, чтобы закрыть и освободить соединение, ранее открытое в методе <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>.  
  
```vb  
    Dim connMgr As IDTSConnectionManager100  
...  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
```  
  
```csharp  
IDTSConnectionManager100 connMgr;  
  
public override void ReleaseConnections()  
{  
  
    connMgr.ReleaseConnection(sqlConn);  
  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Настройка компонента скрипта в редакторе компонентов скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)   
 [Кодирование и отладка компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  


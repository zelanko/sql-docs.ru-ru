---
title: Написание кода пользовательского перечислителя по каждому элементу | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services], coding
ms.assetid: 279cf6de-d06f-40e7-b8ca-569310449f36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f1edd30c7891b830063b4dc344a353c968342a51
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85427521"
---
# <a name="coding-a-custom-foreach-enumerator"></a>Написание кода пользовательского перечислителя по каждому элементу
  После создания класса, наследующего от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>, и применения к нему атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>, необходимо переопределить реализацию свойств и методов базового класса, чтобы обеспечить пользовательские функциональные возможности.  
  
 Рабочий образец пользовательского перечислителя см. в разделе [Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу](developing-a-user-interface-for-a-custom-foreach-enumerator.md).  
  
## <a name="initializing-the-enumerator"></a>Инициализация перечислителя  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A> можно переопределить для кэширования ссылок на диспетчеры соединений, определенные в пакете, и на интерфейс событий, который можно использовать для формирования ошибок, предупреждений и информационных сообщений.  
  
## <a name="validating-the-enumerator"></a>Проверка перечислителя  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> переопределяется для проверки правильности настройки перечислителя. Если этот метод возвращает значение `Failure`, то перечислитель не будет выполнен в содержащем его пакете. Реализация данного метода индивидуальна для каждого перечислителя, но если перечислитель опирается на объект <xref:Microsoft.SqlServer.Dts.Runtime.Variable> или <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, то необходимо добавить код для проверки наличия этих объектов в коллекции, переданной методу.  
  
 Следующий пример кода иллюстрирует реализацию метода <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A>, который проверяет переменную, указанную в свойстве перечислителя.  
  
```csharp  
private string variableNameValue;  
  
public string VariableName  
{  
    get{ return this.variableNameValue; }  
    set{ this.variableNameValue = value; }  
}  
  
public override DTSExecResult Validate(Connections connections, VariableDispenser variableDispenser, IDTSInfoEvents infoEvents, IDTSLogging log)  
{  
    if (!variableDispenser.Contains(this.variableNameValue))  
    {  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + this.variableNameValue + " does not exist in the collection.", "", 0);  
            return DTSExecResult.Failure;  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Private variableNameValue As String  
  
Public Property VariableName() As String  
    Get   
         Return Me.variableNameValue  
    End Get  
    Set (ByVal Value As String)   
         Me.variableNameValue = value  
    End Set  
End Property  
  
Public Overrides Function Validate(ByVal connections As Connections, ByVal variableDispenser As VariableDispenser, ByVal infoEvents As IDTSInfoEvents, ByVal log As IDTSLogging) As DTSExecResult  
    If Not variableDispenser.Contains(Me.variableNameValue) Then  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + Me.variableNameValue + " does not exist in the collection.", "", 0)  
            Return DTSExecResult.Failure  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
## <a name="returning-the-collection"></a>Возврат коллекции  
 В процессе выполнения контейнер <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> вызывает метод пользовательского перечислителя <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>. В этом методе перечислитель создает и заполняет коллекцию элементов, после чего возвращает эту коллекцию. Затем объект <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> последовательно перебирает элементы коллекции и выполняет поток управления для каждого элемента коллекции.  
  
 Следующий пример иллюстрирует реализацию метода <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>, который возвращает массив случайных значений.  
  
```csharp  
public override object GetEnumerator()  
{  
    ArrayList numbers = new ArrayList();  
  
    Random randomNumber = new Random(DateTime.Now);  
  
    for( int x=0; x < 100; x++ )  
        numbers.Add( randomNumber.Next());  
  
    return numbers;  
}  
```  
  
```vb  
Public Overrides Function GetEnumerator() As Object  
    Dim numbers As ArrayList =  New ArrayList()   
  
    Dim randomNumber As Random =  New Random(DateTime.Now)   
  
        Dim x As Integer  
        For  x = 0 To  100- 1  Step  x + 1  
        numbers.Add(randomNumber.Next())  
        Next  
  
    Return numbers  
End Function  
```  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского перечислителя Foreach](creating-a-custom-foreach-enumerator.md)   
 [Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  

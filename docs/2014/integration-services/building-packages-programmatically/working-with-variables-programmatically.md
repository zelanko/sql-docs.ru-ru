---
title: Программная работа с переменными | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System namespace
- scope [Integration Services]
- variables [Integration Services], programmatically
- configuration files [Integration Services]
- Variables collection
- User namespace
- custom variables [Integration Services]
- variables [Integration Services], customizing
ms.assetid: c4b76a3d-94ca-4a8e-bb45-cb8bd0ea3ec1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4833ee0dd6514b6a05118b80b756c5fd2de069a3
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58377488"
---
# <a name="working-with-variables-programmatically"></a>Программная работа с переменными
  С помощью переменных можно динамически задавать значения и управлять процессами в пакетах, контейнерах, задачах и обработчиках событий. Переменные могут также использоваться элементами управления очередностью для управления направлением потока данных к различным задачам. С помощью переменных можно:  
  
-   Обновлять свойства пакета во время выполнения.  
  
-   Заполнять значения параметров инструкций Transact-SQL во время выполнения.  
  
-   Управлять потоком цикла по каждому элементу. Дополнительные сведения см. в разделе [Добавление перечисления к потоку управления](../control-flow/control-flow.md).  
  
-   Управлять управлением очередностью, используя его в выражении. Управление очередностью может содержать переменные в определении ограничения. Дополнительные сведения см. в статье [Добавление выражений к элементам управления очередностью](../control-flow/precedence-constraints.md).  
  
-   Управлять условным повторением контейнера «цикл по элементам». Дополнительные сведения см. в разделе [Добавление итерации к потоку управления](../add-iteration-to-a-control-flow.md).  
  
-   Строить выражения, содержащие значения переменных.  
  
-   Пользователь может создать пользовательские переменные для всех типов контейнеров: пакетов, контейнеров **цикл по каждому элементу**, контейнеров **цикл по элементам**, контейнеров **последовательности**, серверов задач и обработчиков событий. Дополнительные сведения см. в разделах [Переменные в службах Integration Services (SSIS)](../integration-services-ssis-variables.md) и [Использование переменных в пакетах](../use-variables-in-packages.md).  
  
## <a name="scope"></a>Область действия  
 Каждый контейнер имеет собственную коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.Variables>. При создании новой переменной она располагается в области своего родительского контейнера. Поскольку контейнер пакета находится на верхнем уровне иерархии контейнеров, переменные в области пакета ведут себя как глобальные переменные и могут использоваться во всех контейнерах пакета. Доступ к коллекции переменных для контейнера могут также получать дочерние элементы контейнера через коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.Variables>, используя имя переменной или ее индекс в коллекции.  
  
 Поскольку доступность переменной определяется сверху вниз, переменные, объявленные на уровне пакета, являются доступными для всех контейнеров в пакете. Таким образом, коллекция <xref:Microsoft.SqlServer.Dts.Runtime.Variables> в контейнере включает все переменные, принадлежащие родительской коллекции, в дополнение к своим собственным.  
  
 С другой стороны, переменные, содержащиеся в задаче, ограничены по области применения и доступности и доступны только задаче.  
  
 Если пакет выполняет другие пакеты, переменные, определенные в области вызывающего пакета, доступны для вызываемого пакета. Единственным исключением является случай, когда в вызываемом пакете существует переменная с тем же именем. При возникновении такой коллизии значение переменной из вызываемого пакета переопределяет значение переменной из вызывающего пакета. Переменные, определенные в области вызываемого пакета, недоступны для вызывающего пакета.  
  
 В следующем примере кода программным способом создается переменная `myCustomVar` в области пакета, а затем просматриваются все переменные, доступные для пакета, выводятся на печать их имена, тип данных и значения.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application app = new Application();  
      // Load a sample package that contains a variable that sets the file name.  
      Package pkg = app.LoadPackage(  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx",  
        null);  
      Variables pkgVars = pkg.Variables;  
      Variable myVar = pkg.Variables.Add("myCustomVar", false, "User", "3");  
      foreach (Variable pkgVar in pkgVars)  
      {  
        Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name,  
          pkgVar.DataType, pkgVar.Value.ToString());  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim app As Application = New Application()  
    ' Load a sample package that contains a variable that sets the file name.  
    Dim pkg As Package = app.LoadPackage( _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx", _  
      Nothing)  
    Dim pkgVars As Variables = pkg.Variables  
    Dim myVar As Variable = pkg.Variables.Add("myCustomVar", False, "User", "3")  
    Dim pkgVar As Variable  
    For Each pkgVar In pkgVars  
      Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name, _  
        pkgVar.DataType, pkgVar.Value.ToString())  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Образец вывода:**  
  
 `Variable: CancelEvent, Int32, 0`  
  
 `Variable: CreationDate, DateTime, 4/18/2003 11:57:00 AM`  
  
 `Variable: CreatorComputerName, String,`  
  
 `Variable: CreatorName, String,`  
  
 `Variable: ExecutionInstanceGUID, String, {237AB5A4-7E59-4FC9-8D61-E8F20363DF25}`  
  
 `Variable: FileName, String, Junk`  
  
 `Variable: InteractiveMode, Boolean, False`  
  
 `Variable: LocaleID, Int32, 1033`  
  
 `Variable: MachineName, String, MYCOMPUTERNAME`  
  
 `Variable: myCustomVar, String, 3`  
  
 `Variable: OfflineMode, Boolean, False`  
  
 `Variable: PackageID, String, {F0D2E396-A6A5-42AE-9467-04CE946A810C}`  
  
 `Variable: PackageName, String, DTSPackage1`  
  
 `Variable: StartTime, DateTime, 1/28/2005 7:55:39 AM`  
  
 `Variable: UserName, String, <domain>\<userid>`  
  
 `Variable: VersionBuild, Int32, 198`  
  
 `Variable: VersionComments, String,`  
  
 `Variable: VersionGUID, String, {90E105B4-B4AF-4263-9CBD-C2050C2D6148}`  
  
 `Variable: VersionMajor, Int32, 1`  
  
 `Variable: VersionMinor, Int32, 0`  
  
 Обратите внимание, что все переменные, определенные в пространстве имен **System**, доступны для пакета. Дополнительные сведения см. в статье [System Variables](../system-variables.md).  
  
## <a name="namespaces"></a>Пространства имен  
 Службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) предоставляют два пространства имен по умолчанию, в которых располагаются переменные, — **User** и **System**. По умолчанию любая пользовательская переменная, созданная разработчиком, добавляется в пространство имен **User**. Системные переменные располагаются в пространстве имен **System**. Можно создавать дополнительные пространства имен, отличные от **User**, для размещения пользовательских переменных. Также можно изменить имя пространства имен **User**. В то же время нельзя добавить или изменить переменные в пространстве имен **System** или назначить системные переменные другому пространству имен.  
  
 Доступность системных переменных определяется типом контейнера. Список системных переменных, доступных для пакетов, контейнеров, задач и обработчиков событий, см. в разделе [Системные переменные](../system-variables.md).  
  
## <a name="value"></a>Значение  
 Значением пользовательской переменной может быть строка или выражение.  
  
-   Если необходимо задать для переменной литеральное значение, укажите значение ее свойства <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A>.  
  
-   Если необходимо, чтобы переменная содержала выражение, результаты которого использовались бы в качестве ее значения, присвойте свойству <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> переменной значение `true` и предоставьте выражение в свойстве <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A>. Во время выполнения выражение вычисляется, и его результат используется в качестве значения переменной. Например, если свойство выражения переменной имеет вид `"100 * 2""100 * 2"`, в результате вычисления переменная получает значение 200.  
  
 Для переменной нельзя явно задать значение <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A>. Значение <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> выводится из исходного значения, присвоенного переменной, и в дальнейшем не может быть изменено. Дополнительные сведения о типах данных переменных см. в разделе [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md).  
  
 В следующем примере кода создается новая переменная, свойству <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> присваивается значение `true`, выражение `"100 * 2"` назначается в качестве значения свойства Expression переменной, а затем выводится значение переменной.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package pkg = new Package();  
      Variable v100 = pkg.Variables.Add("myVar", false, "", 1);  
      v100.EvaluateAsExpression = true;  
      v100.Expression = "100 * 2";  
      Console.WriteLine("Expression for myVar: {0}",   
        v100.Properties["Expression"].GetValue(v100));  
      Console.WriteLine("Value of myVar: {0}", v100.Value.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkg As Package = New Package  
    Dim v100 As Variable = pkg.Variables.Add("myVar", False, "", 1)  
    v100.EvaluateAsExpression = True  
    v100.Expression = "100 * 2"  
    Console.WriteLine("Expression for myVar: {0}", _  
      v100.Properties("Expression").GetValue(v100))  
    Console.WriteLine("Value of myVar: {0}", v100.Value.ToString)  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Образец вывода:**  
  
 `Expression for myVar: 100 * 2`  
  
 `Value of myVar: 200`  
  
 Выражение должно быть действительным выражением, использующим синтаксис выражений служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Литералы допускаются в выражениях переменных, в дополнение к операторам и функциям, которые предоставляются синтаксисом выражений, однако выражения не могут ссылаться на другие переменные или столбцы. Дополнительные сведения см. в разделе [Выражения служб Integration Services (SSIS)](../expressions/integration-services-ssis-expressions.md).  
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Если в файле конфигурации содержится пользовательская переменная, эта переменная может быть обновлена во время выполнения. Это означает, что при выполнении пакета значение переменной, содержавшееся в пакете изначально, заменяется новым значением из файла конфигурации. Такой способ замены оказывается полезным, когда пакет развертывается на нескольких серверах, где требуются разные значения переменной. Например, переменная может содержать число повторений рабочего процесса контейнера **цикл по каждому элементу**, список получателей, которым обработчик событий направляет сообщения электронной почты при возникновении ошибки, либо измененное максимально допустимое число ошибок перед завершением выполнения пакета со сбоем. Эти переменные динамически передаются в файлах конфигурации для каждой среды. По этой причине в файлах конфигурации допускается использование только переменных, доступных для чтения и записи. Дополнительные сведения см. в разделе [Создание конфигурации пакетов](../create-package-configurations.md).  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Переменные в службах Integration Services (SSIS)](../integration-services-ssis-variables.md)   
 [Использование переменных в пакетах](../use-variables-in-packages.md)  
  
  

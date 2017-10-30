---
title: "Создание назначения с помощью компонента скрипта | Документы Microsoft"
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
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7680aac73590f92eadd615b9d164967e61877664
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-destination-with-the-script-component"></a>Создание назначения с помощью компонента скрипта
  Компонент назначения в потоке данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используется для сохранения данных, полученных из вышестоящих источников и преобразований, в источник данных. Обычно компонент назначения подключается к источнику данных через существующий диспетчер соединений.  
  
 Обзор компонента скрипта см. в разделе [расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Компонент скрипта и формируемый им код инфраструктуры значительно упрощают процесс создания пользовательских компонентов потока данных. Тем не менее, чтобы понять, как работает компонент скрипта, вам может быть полезно ознакомиться с шагами по разработке пользовательских компонентов потока данных в [разработке пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) раздела и особенно [Разработка пользовательского компонента назначения](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).  
  
## <a name="getting-started-with-a-destination-component"></a>Приступая к работе с компонентом назначения  
 При добавлении компонента скрипта на вкладку «поток данных» [!INCLUDE[ssIS](../../includes/ssis-md.md)] конструкторе **Выбор типа компонента скрипта** диалоговое окно, вам будет предложено выбрать **источника**, **назначения** , или **преобразования** сценария. В этом диалоговом окне выберите **назначения**.  
  
 Затем подключите выход преобразования к компоненту назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Для целей тестирования можно напрямую соединить источник с назначением без преобразований.  
  
## <a name="configuring-a-destination-component-in-metadata-design-mode"></a>Настройка компонента назначения в режиме конструктора метаданных  
 Выбрав параметр для создания компонента назначения, настроить компонент с помощью **редактор преобразования «скрипт»**. Дополнительные сведения см. в разделе [Настройка компонента скрипта в редакторе компонентов скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Выберите язык сценария, который будет использоваться назначением скрипта, задайте **ScriptLanguage** свойство **сценарий** страница **редактор преобразования «скрипт»** диалоговое окно.  
  
> [!NOTE]  
>  Чтобы задать значение по умолчанию языка скрипта для компонента скрипта, используйте **язык сценариев** параметр **Общие** страница **параметры** диалоговое окно. Дополнительные сведения см. в разделе [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Компонент назначения потока данных имеет один вход и ни одного выхода. Настройка входа компонента — один из шагов, которые необходимо выполнить в режиме конструктора метаданных с помощью **редактор преобразования «скрипт»**, прежде чем писать пользовательский скрипт.  
  
### <a name="adding-connection-managers"></a>Добавление диспетчеров соединений  
 Обычно компонент назначения через существующий диспетчер соединений подключается к источнику данных, куда сохраняет данные из потока данных. На **диспетчеры соединений** страница **редактор преобразования «скрипт»**, нажмите кнопку **добавить** добавить нужный диспетчер соединений.  
  
 Однако диспетчер соединений представляет собой лишь удобную оболочку, которая инкапсулирует и хранит информацию, нужную для подключения к источнику данных определенного типа. Для загрузки и сохранения данных, и, возможно, также для открытия и закрытия соединения с источником данных нужно разрабатывать собственный код.  
  
 Общие сведения об использовании диспетчеров соединений в компоненте скрипта см. в разделе [соединения с источниками данных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
 Дополнительные сведения о **диспетчеры соединений** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; Страница «Диспетчеры соединений» &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-inputs-and-input-columns"></a>Настройка входов и входных столбцов  
 Компонент назначения имеет один вход и ни одного выхода.  
  
 На **входные столбцы** страница **редактор преобразования «скрипт»**, список столбцов содержит доступные столбцы из выходных данных вышестоящего компонента потока данных. Выберите столбцы, которые нужно сохранить.  
  
 Дополнительные сведения о **входные столбцы** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; страницы столбцы входных данных &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
 **Входы и выходы** страница **редактор преобразования «скрипт»** показывает один вход, можно переименовать. В скрипте можно ссылаться на столбец ввода по имени с помощью свойства метода доступа, созданного автоматически.  
  
 Дополнительные сведения о **входы и выходы** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; входов и выходов страницу &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Добавление переменных  
 Если вы хотите использовать существующих переменных в сценарии, можно добавить их в **ReadOnlyVariables** и **ReadWriteVariables** поля свойств на **сценарий** страницы **Редактор преобразования «скрипт»**.  
  
 Если в поле свойства добавляются несколько переменных, их имена нужно разделять запятыми. Можно также выбрать несколько переменных, нажав кнопку с многоточием (**...** ) рядом с **ReadOnlyVariables** и **ReadWriteVariables** поля свойств, а затем выбрав переменные в **Выбор переменных** диалоговое окно.  
  
 Общие сведения об использовании переменных в компоненте скрипта см. в разделе [использование переменных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Дополнительные сведения о **сценарий** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; Страница «скрипт» &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-destination-component-in-code-design-mode"></a>Создание скрипта для компонента назначения в режиме конструктора кода  
 После настройки метаданных для компонента можно написать пользовательский скрипт. В **редактор преобразования «скрипт»**на **сценарий** щелкните **изменить скрипт** Открытие [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA) интегрированной среды разработки где можно добавить пользовательский скрипт. Язык сценариев, который вы используете зависит от того, можно выбрать [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# как язык скриптов для **ScriptLanguage** свойство **сценария** страница.  
  
 Важные сведения, относящиеся ко всем типам компонентов, созданных с помощью компонента скрипта см. в разделе [кодировании и отладке компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Основные сведения об автоматически создаваемом коде  
 При открытии интегрированной среды разработки VSTA после создания и настройки компонента назначения, редактируемый **ScriptMain** класс появится в редакторе кода с заглушкой для **ProcessInputRow** метод. **ScriptMain** используется класс будет написания собственного кода, и **ProcessInputRow** является наиболее важным методом в компоненте назначения.  
  
 При открытии **обозревателя проектов** окна в VSTA, можно увидеть, что компонент скрипта также создал только для чтения **BufferWrapper** и **ComponentWrapper** проекта элементы. **ScriptMain** класс наследует от **UserComponent** класса в **ComponentWrapper** элемент проекта.  
  
 Во время выполнения подсистема обработки потока данных вызывает **ProcessInput** метод в **UserComponent** класс, переопределяющий <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> родительского класса. **ProcessInput** метод в свою очередь выполняет цикл по строкам во входном буфере и вызывает **ProcessInputRow** метод один раз для каждой строки.  
  
### <a name="writing-your-custom-code"></a>Написание пользовательского кода  
 Чтобы завершить создание пользовательского компонента назначения, может потребоваться написать скрипт в следующие методы, доступные в **ScriptMain** класса.  
  
1.  Переопределить **AcquireConnections** способ подключения к внешнему источнику данных. Извлеките из диспетчера соединений объект соединения или необходимые сведения о соединении.  
  
2.  Переопределить **PreExecute** метод для подготовки для сохранения данных. Например, может потребоваться создать и настроить **SqlCommand** и его параметры в этом методе.  
  
3.  Используйте переопределенный **ProcessInputRow** метод для копирования каждой входной строки с внешним источником данных. Например, для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения, можно скопировать значения столбцов в параметры **SqlCommand** и выполните следующую команду один раз для каждой строки. Для назначения неструктурированного файла, можно записать значения для каждого столбца, чтобы **StreamWriter**, разделяя значения разделителем столбцов.  
  
4.  Переопределить **PostExecute** метод для отключения от внешнего источника данных, при необходимости и выполнить необходимую очистку.  
  
## <a name="examples"></a>Примеры  
 Примеры демонстрируют код, необходимый в **ScriptMain** класса, чтобы создать компонент назначения.  
  
> [!NOTE]  
>  В этих примерах используются **Person.Address** в таблицу **AdventureWorks** образца базы данных и передается ее первый и четвертый столбец  **int*AddressID* ** и **Город nvarchar (30)** поток данных. Эти же данные используются в образцах источника, преобразования и назначения, приведенных в этом разделе. Для каждого примера приведены необходимые дополнительные условия и принимаемые предположения.  
  
### <a name="adonet-destination-example"></a>Пример назначения ADO.NET  
 В этом примере демонстрируется компонент назначения, пользующихся существующими [!INCLUDE[vstecado](../../includes/vstecado-md.md)] диспетчер соединений для сохранения данных из потока данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу.  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Создание [!INCLUDE[vstecado](../../includes/vstecado-md.md)] диспетчер соединений, который использует **SqlClient** поставщик для подключения к **AdventureWorks** базы данных.  
  
2.  Создайте целевую таблицу, выполнив следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] в **AdventureWorks** базы данных:  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве назначения.  
  
4.  Соедините выход источника или преобразования, расположенного выше в потоке данных, с компонентом назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Этот вывод должен предоставлять данные из **Person.Address** таблицу **AdventureWorks** образца базы данных, который содержит по крайней мере **AddressID** и  **Город** столбцов.  
  
5.  Откройте **редактор преобразования «скрипт»**. На **входные столбцы** выберите **AddressID** и **Город** входные столбцы.  
  
6.  На **входы и выходы** страницы, например, измените имя входа на более описательное имя **MyAddressInput**.  
  
7.  На **диспетчеры соединений** добавьте или создайте [!INCLUDE[vstecado](../../includes/vstecado-md.md)] диспетчер соединений с именем, например **MyADONETConnectionManager**.  
  
8.  На **сценарий** щелкните **изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скрипта.  
  
9. Закрыть **редактор преобразования «скрипт»** и выполнение образца.  
  
```vb  
Imports System.Data.SqlClient  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim connMgr As IDTSConnectionManager100  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        connMgr = Me.Connections.MyADONETConnectionManager  
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
        With sqlCmd  
            .Parameters("@addressid").Value = Row.AddressID  
            .Parameters("@city").Value = Row.City  
            .ExecuteNonQuery()  
        End With  
    End Sub  
  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.Data.SqlClient;  
public class ScriptMain:  
    UserComponent  
  
{  
    IDTSConnectionManager100 connMgr;  
    SqlConnection sqlConn;  
    SqlCommand sqlCmd;  
    SqlParameter sqlParam;  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        connMgr = this.Connections.MyADONETConnectionManager;  
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +  
            "VALUES(@addressid, @city)", sqlConn);  
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);  
        sqlCmd.Parameters.Add(sqlParam);  
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);  
        sqlCmd.Parameters.Add(sqlParam);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
        {  
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;  
            sqlCmd.Parameters["@city"].Value = Row.City;  
            sqlCmd.ExecuteNonQuery();  
        }  
    }  
  
    public override void ReleaseConnections()  
    {  
  
        connMgr.ReleaseConnection(sqlConn);  
  
    }  
  
}  
```  
  
### <a name="flat-file-destination-example"></a>Пример назначения «Неструктурированный файл»  
 В этом примере показан компонент назначения, который с помощью существующего диспетчера соединений с неструктурированными файлами сохраняет данные из потока данных в неструктурированный файл.  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Создайте диспетчер соединений с неструктурированными файлами, соединяющийся с целевым файлом. Файл может не существовать; компонент назначения создаст его. Настройте файл назначения как файл с разделителями запятыми, содержащий **AddressID** и **Город** столбцов.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве назначения.  
  
3.  Соедините выход источника или преобразования, расположенного выше в потоке данных, с компонентом назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Этот вывод должен предоставлять данные из **Person.Address** таблицу **AdventureWorks** образца базы данных и должно содержать по крайней мере **AddressID** и **Города** столбцов.  
  
4.  Откройте **редактор преобразования «скрипт»**. На **входные столбцы** выберите **AddressID** и **Город** столбцов.  
  
5.  На **входы и выходы** страницы, измените имя входа на более описательное имя, например **MyAddressInput**.  
  
6.  На **диспетчеры соединений** добавьте или создайте неструктурированного файла диспетчер соединений с понятным именем, например **MyFlatFileDestConnectionManager**.  
  
7.  На **сценарий** щелкните **изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скрипта.  
  
8.  Закрыть **редактор преобразования «скрипт»** и выполнение образца.  
  
```vb  
Imports System.IO  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim copiedAddressFile As String  
    Private textWriter As StreamWriter  
    Private columnDelimiter As String = ","  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        Dim connMgr As IDTSConnectionManager100 = _  
            Me.Connections.MyFlatFileDestConnectionManager  
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        textWriter = New StreamWriter(copiedAddressFile, False)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With textWriter  
            If Not Row.AddressID_IsNull Then  
                .Write(Row.AddressID)  
            End If  
            .Write(columnDelimiter)  
            If Not Row.City_IsNull Then  
                .Write(Row.City)  
            End If  
            .WriteLine()  
        End With  
  
    End Sub  
  
    Public Overrides Sub PostExecute()  
  
        textWriter.Close()  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.IO;  
public class ScriptMain:  
    UserComponent  
  
{  
    string copiedAddressFile;  
    private StreamWriter textWriter;  
    private string columnDelimiter = ",";  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;  
        copiedAddressFile = (string) connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        textWriter = new StreamWriter(copiedAddressFile, false);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            if (!Row.AddressID_IsNull)  
            {  
                textWriter.Write(Row.AddressID);  
            }  
            textWriter.Write(columnDelimiter);  
            if (!Row.City_IsNull)  
            {  
                textWriter.Write(Row.City);  
            }  
            textWriter.WriteLine();  
        }  
  
    }  
  
    public override void PostExecute()  
    {  
  
        textWriter.Close();  
  
    }  
  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание источника с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)   
 [Разработка пользовательского компонента назначения](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
  
  


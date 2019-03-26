---
title: Создание назначения с помощью компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6a23c9ece7522d2b7785b77789ba9e87b5ef356c
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271623"
---
# <a name="creating-a-destination-with-the-script-component"></a>Создание назначения с помощью компонента скрипта
  Компонент назначения в потоке данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используется для сохранения данных, полученных из вышестоящих источников и преобразований, в источник данных. Обычно компонент назначения подключается к источнику данных через существующий диспетчер соединений.  
  
 Общие сведения о компоненте скрипта см. в разделе [Расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Компонент скрипта и формируемый им код инфраструктуры значительно упрощают процесс создания пользовательских компонентов потока данных. Однако чтобы понять, как работает компонент скрипта, может быть полезно ознакомиться с шагами по разработке пользовательских компонентов потока данных, описанными в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) и в особенности в разделе [Разработка пользовательского компонента назначения](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).  
  
## <a name="getting-started-with-a-destination-component"></a>Приступая к работе с компонентом назначения  
 При добавлении компонента скрипта на вкладку "Поток данных" конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] открывается диалоговое окно **Выбор типа компонента скрипта** с приглашением выбрать скрипт **Источник**, **Назначение** или **Преобразование**. Выберите в этом диалоговом окне скрипт **Назначение**.  
  
 Затем подключите выход преобразования к компоненту назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Для целей тестирования можно напрямую соединить источник с назначением без преобразований.  
  
## <a name="configuring-a-destination-component-in-metadata-design-mode"></a>Настройка компонента назначения в режиме конструктора метаданных  
 Выбрав параметр создания компонента назначения, можно настроить его с помощью **редактора преобразования "Скрипт"**. Дополнительные сведения см. в разделе [Настройка компонента скрипта в редакторе компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Чтобы выбрать язык скрипта в назначении скрипта, нужно задать свойство **ScriptLanguage** на странице **Скрипт** диалогового окна **Редактор преобразования "Скрипт"**.  
  
> [!NOTE]  
>  Чтобы установить язык скрипта по умолчанию для компонента скрипта, воспользуйтесь параметром **Язык сценариев** на странице **Общие** диалогового окна **Параметры**. Дополнительные сведения см. в разделе [General Page](../general-page-of-integration-services-designers-options.md).  
  
 Компонент назначения потока данных имеет один вход и ни одного выхода. Настройка входа компонента является одним из шагов, которые необходимо выполнить в режиме конструктора метаданных с использованием **редактора преобразования "Скрипт"**, прежде чем приступать к написанию пользовательского скрипта.  
  
### <a name="adding-connection-managers"></a>Добавление диспетчеров соединений  
 Обычно компонент назначения через существующий диспетчер соединений подключается к источнику данных, куда сохраняет данные из потока данных. На странице **Диспетчеры соединений** в **редакторе преобразования "Скрипт"** нажмите кнопку **Добавить**, чтобы добавить нужный диспетчер соединений.  
  
 Однако диспетчер соединений представляет собой лишь удобную оболочку, которая инкапсулирует и хранит информацию, нужную для подключения к источнику данных определенного типа. Для загрузки и сохранения данных, и, возможно, также для открытия и закрытия соединения с источником данных нужно разрабатывать собственный код.  
  
 Общие сведения об использовании диспетчеров соединений в компоненте скрипта см. в разделе [Соединение с источниками данных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
 Дополнительные сведения о странице **Диспетчеры соединений** окна **Редактор преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Диспетчеры соединений")](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-inputs-and-input-columns"></a>Настройка входов и входных столбцов  
 Компонент назначения имеет один вход и ни одного выхода.  
  
 На странице **Входные столбцы** в **редакторе преобразования "Скрипт"** список столбцов содержит доступные столбцы на выходе вышестоящего компонента в потоке данных. Выберите столбцы, которые нужно сохранить.  
  
 Дополнительные сведения о странице **Входные столбцы** **редактора преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Входные столбцы")](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
 Страница **Входы и выходы** диалогового окна **Редактор преобразования "Скрипт"** показывает один вход, который можно переименовать. В скрипте можно ссылаться на столбец ввода по имени с помощью свойства метода доступа, созданного автоматически.  
  
 Дополнительные сведения о странице **Входы и выходы** **редактора преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Входы и выходы")](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Добавление переменных  
 Если нужно использовать в скрипте значения существующих переменных, их можно добавить в поля свойств **ReadOnlyVariables** и **ReadWriteVariables** на странице **Скрипт** в **редакторе преобразования "Скрипт"**.  
  
 Если в поле свойства добавляются несколько переменных, их имена нужно разделять запятыми. Также можно выбрать несколько переменных, нажав кнопку с многоточием (**…**), расположенную рядом с полями свойств **ReadOnlyVariables** и **ReadWriteVariables**, а затем выбрав переменные в диалоговом окне **Выбор переменных**.  
  
 Общие сведения об использовании переменных в компоненте скрипта см. в разделе [Использование переменных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Дополнительные сведения о странице **Скрипт** в окне **Редактор преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Скрипт")](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-destination-component-in-code-design-mode"></a>Создание скрипта для компонента назначения в режиме конструктора кода  
 После настройки метаданных для компонента можно написать пользовательский скрипт. В **редакторе преобразования "Скрипт"** на странице **Скрипт** нажмите кнопку **Изменить скрипт**, чтобы открыть интегрированную среду разработки средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA), где можно добавить пользовательский скрипт. Используемый язык скриптов зависит от значения свойства **ScriptLanguage**, указанного на странице **Скрипт**. В качестве значения можно выбрать язык [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Важные сведения, относящиеся ко всем типам компонентов, создаваемым с помощью компонента скрипта, см. в разделе [Кодирование и отладка компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Основные сведения об автоматически создаваемом коде  
 При открытии интегрированной среды разработки VSTA после создания и настройки компонента назначения изменяемый класс **ScriptMain** отображается в редакторе кода с заглушкой для метода **ProcessInputRow**. Пользовательский код создается в классе **ScriptMain**, а самым важным методом в компоненте назначения является **ProcessInputRow**.  
  
 Если открыть окно **Обозреватель проектов** в VSTA, можно увидеть, что для компонента скрипта также были созданы элементы проекта **BufferWrapper** и **ComponentWrapper**, доступные только для чтения. Класс **ScriptMain** наследуется от класса **UserComponent** в элементе проекта **ComponentWrapper**.  
  
 Во время выполнения подсистема обработки потоков данных вызывает метод **ProcessInput** в классе **UserComponent**, переопределяющий метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> родительского класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. В свою очередь, метод **ProcessInput** проходит по строкам во входном буфере и вызывает для каждой строки метод **ProcessInputRow**.  
  
### <a name="writing-your-custom-code"></a>Написание пользовательского кода  
 Для завершения пользовательского компонента назначения можно ввести скрипты в следующие методы, доступные в классе **ScriptMain**.  
  
1.  Переопределите метод **AcquireConnections** для соединения с внешним источником данных. Извлеките из диспетчера соединений объект соединения или необходимые сведения о соединении.  
  
2.  Для подготовки к сохранению данных переопределите метод **PreExecute**. Например, в этом методе можно создать и настроить объект **SqlCommand** и его параметры.  
  
3.  Используйте переопределенный метод **ProcessInputRow** для копирования всех строк ввода во внешний источник данных. Например, для назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно скопировать значения столбцов в параметры **SqlCommand** и выполнить команду по одному разу для каждой строки. Для назначения "Неструктурированный файл" можно записать значения столбцов в объект **StreamWriter**, разделяя значения разделителем столбцов.  
  
4.  Переопределите метод **PostExecute** для отключения от внешнего источника данных, если это требуется, и для выполнения всех прочих действий по очистке.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры демонстрируют код, нужный классу **ScriptMain** для создания компонента назначения.  
  
> [!NOTE]
>  В этих примерах используется таблица **Person.Address** из примера базы данных **AdventureWorks**. В поток данных передаются ее первый и четвертый столбцы: **int*AddressID*** и **nvarchar(30)City**. Эти же данные используются в образцах источника, преобразования и назначения, приведенных в этом разделе. Для каждого примера приведены необходимые дополнительные условия и принимаемые предположения.  
  
### <a name="adonet-destination-example"></a>Пример назначения ADO.NET  
 В этом примере показан компонент назначения, который с помощью существующего диспетчера подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] сохраняет данные из потока данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Создайте диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)], использующий поставщик **SqlClient** для соединения с базой данных **AdventureWorks**.  
  
2.  Создайте целевую таблицу, запустив следующую команду [!INCLUDE[tsql](../../includes/tsql-md.md)] в базе данных **AdventureWorks**:  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве назначения.  
  
4.  Соедините выход источника или преобразования, расположенного выше в потоке данных, с компонентом назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Этот выход должен содержать данные из таблицы **Person.Address** образца базы данных **AdventureWorks**, которая содержит по крайней мере столбцы **AddressID** и **City**.  
  
5.  Откройте **редактор преобразования "Скрипт"**. На странице **Входные столбцы** выберите входные столбцы **AddressID** и **City**.  
  
6.  На странице **Входы и выходы** измените имя входа на более описательное, например **ВходАдреса**.  
  
7.  На странице **Диспетчеры соединений** добавьте или создайте диспетчер подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] с описательным именем, например **MyADONETConnectionManager**.  
  
8.  На странице **Скрипт** нажмите кнопку **Изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скрипта.  
  
9. Закройте **редактор преобразования "Скрипт"** и запустите образец.  
  
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
  
1.  Создайте диспетчер соединений с неструктурированными файлами, соединяющийся с целевым файлом. Файл может не существовать; компонент назначения создаст его. Настройте файл назначения как файл с разделителями-запятыми, содержащий столбцы **AddressID** и **City**.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве назначения.  
  
3.  Соедините выход источника или преобразования, расположенного выше в потоке данных, с компонентом назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Этот вывод должен предоставлять данные из таблицы **Person.Address** образца базы данных **AdventureWorks** и содержать по крайней мере столбцы **AddressID** и **City**.  
  
4.  Откройте **редактор преобразования "Скрипт"**. На странице **Входные столбцы** выберите столбцы **AddressID** и **City**.  
  
5.  На странице **Входы и выходы** измените имя входа на более описательное, например **ВходАдреса**.  
  
6.  На странице **Диспетчеры соединений** добавьте или создайте диспетчер подключений к неструктурированным файлам с описательным именем, например **MyFlatFileDestConnectionManager**.  
  
7.  На странице **Скрипт** нажмите кнопку **Изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скрипта.  
  
8.  Закройте **редактор преобразования "Скрипт"** и запустите образец.  
  
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
  
  

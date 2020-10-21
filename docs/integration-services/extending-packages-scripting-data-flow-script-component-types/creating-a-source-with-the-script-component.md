---
description: Создание источника с помощью компонента скрипта
title: Создание источника с помощью компонента скрипта | Документы Майкрософт
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
- Script component [Integration Services], source components
- output columns [Integration Services]
- sources [Integration Services], components
ms.assetid: 547c4179-ea82-4265-8c6f-04a2aa77a3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19fe9c40aa87d4ee1cdc7b719e06911de9a1f167
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193144"
---
# <a name="creating-a-source-with-the-script-component"></a>Создание источника с помощью компонента скрипта

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Компонент источника в потоке данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно использовать для загрузки данных из источника данных для передачи в нижележащие преобразования и назначения. Обычно подключение к источнику данных осуществляется через существующий диспетчер соединений.  
  
 Общие сведения о компоненте скрипта см. в разделе [Расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Компонент скрипта и формируемый им код инфраструктуры значительно упрощают процесс создания пользовательских компонентов потока данных. Однако, чтобы понять работу этого компонента скрипта, может потребоваться ознакомиться с шагами, связанными с разработкой пользовательского компонента потока данных. См. раздел [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) и особенно раздел [Разработка пользовательского компонента источника](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).  
  
## <a name="getting-started-with-a-source-component"></a>Приступая к работе с компонентом источника  
 При добавлении компонента скрипта в область "Поток данных" конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] открывается диалоговое окно **Выбор типа компонента скрипта** с приглашением выбрать скрипт источника, назначения или преобразования. В этом диалоговом окне выберите скрипт **Источник**.  
  
## <a name="configuring-a-source-component-in-metadata-design-mode"></a>Настройка компонента источника в режиме конструктора метаданных  
 После выбора для создания компонента источника необходимо настроить этот компонент с помощью окна **Редактор преобразования "скрипт"** . Дополнительные сведения см. в разделе [Настройка компонента скрипта в редакторе компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Компонент источника потока данных не имеет входов и поддерживает один или несколько выходов. Настройка выходов для компонента представляет собой один из шагов, который должен быть выполнен в режиме конструктора метаданных с помощью окна **Редактор преобразования "скрипт"** до начала написания пользовательского скрипта.  
  
 Можно также указать язык скрипта, задавая свойство **ScriptLanguage** на странице **Скрипт** окна **Редактор преобразования "скрипт"** .  
  
> [!NOTE]  
>  Чтобы установить значение по умолчанию языка скрипта для компонентов скрипта и задач "Скрипт", воспользуйтесь параметром **Язык сценариев** на странице **Общие** диалогового окна **Параметры**. Дополнительные сведения см. в разделе [General Page](~/integration-services/control-flow/script-task-editor-general-page.md).  
  
### <a name="adding-connection-managers"></a>Добавление диспетчеров соединений  
 Как правило, в компоненте источника используется существующий диспетчер соединений для подключения к источнику данных, из которого загружаются данные в поток данных. На странице **Диспетчеры соединений** в **редакторе преобразования "Скрипт"** нажмите кнопку **Добавить**, чтобы добавить нужный диспетчер соединений.  
  
 Но диспетчер соединений представляет собой всего лишь удобный модуль, который инкапсулирует и хранит информацию, необходимую для подключения к источнику данных конкретного типа. Чтобы загрузить или сохранить конкретные данные, необходимо написать собственный пользовательский код, а также, возможно, открыть и закрыть соединение с источником данных.  
  
 Общие сведения об использовании диспетчеров соединений в компоненте скрипта см. в разделе [Соединение с источниками данных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
 Дополнительные сведения о странице **Диспетчеры соединений** окна **Редактор преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Диспетчеры соединений")](../data-flow/transformations/script-component.md).  
  
### <a name="configuring-outputs-and-output-columns"></a>Настройка выходов и выходных столбцов  
 Компонент источника не имеет входов и поддерживает один или несколько выходов. На странице **Входы и выходы** окна **Редактор преобразования "скрипт"** по умолчанию был создан один выход, но не созданы какие-либо выходные столбцы. На этой странице редактора может понадобиться настроить следующие элементы.  
  
-   Необходимо вручную добавить и настроить выходные столбцы для каждого выхода. Выберите папку "Выходные столбцы" для каждого выхода, а затем используйте кнопки **Добавить столбец** и **Удалить столбец**, чтобы управлять выходными столбцами для каждого выхода компонента источника. В дальнейшем можно будет ссылаться на выходные столбцы в скрипте по именам, присвоенным здесь, используя свойства типизированного метода доступа, созданные в автоматически сформированном коде.  
  
-   Может потребоваться создать один или несколько дополнительных выводов, таких как эмулируемый вывод ошибок для строк, содержащих непредвиденные значения. Используйте кнопки **Добавить выход** и **Удалить выход** для управления выходами компонента источника. Все входные строки направляются во все доступные выходы, если только не задано идентичное ненулевое значение для свойства **ExclusionGroup** тех выходов, куда планируется направить каждую строку только для одного из выходов, использующих одно и то же значение **ExclusionGroup**. Конкретное целочисленное значение, выбранное для идентификации группы **ExclusionGroup**, не имеет значения.  
  
    > [!NOTE]  
    >  Также можно использовать ненулевое значение для свойства **ExclusionGroup** с единственным выходом, если не нужно выводить все строки. Однако в этом случае необходимо явно вызывать метод **DirectRowTo\<outputbuffer>** для каждой строки, которую следует отправить на выход.  
  
-   Может потребоваться присвоить выходам понятные имена. В дальнейшем можно будет ссылаться на выходы по их именам в скрипте, используя свойства типизированного метода доступа, созданные в автоматически сформированном коде.  
  
-   Обычно несколько выходов в одной и той же группе **ExclusionGroup** имеют одинаковые выходные столбцы. Однако, если создается моделируемый вывод ошибок, может потребоваться добавить дополнительные столбцы для хранения сведений об ошибках. Сведения об обработке ошибочных строк в подсистеме обработки потока данных см. в разделе [Использование выводов ошибок в компоненте потока данных](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md). Тем не менее в компоненте скрипта необходимо написать собственный код, чтобы заполнить дополнительные столбцы соответствующими сведениями об ошибках. Дополнительные сведения см. в разделе [Имитация вывода ошибок для компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Дополнительные сведения о странице **Входы и выходы** **редактора преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Входы и выходы")](../data-flow/transformations/script-component.md).  
  
### <a name="adding-variables"></a>Добавление переменных  
 Если нужно использовать в скрипте значения существующих переменных, их можно добавить в поля свойств **ReadOnlyVariables** и **ReadWriteVariables** на странице **Скрипт** в **редакторе преобразования "скрипт"** .  
  
 При вводе нескольких переменных в поля свойств разделяйте имена переменных запятыми. Несколько переменных можно также ввести, нажимая кнопку с многоточием ( **...** ) рядом с полями свойств **ReadOnlyVariables** и **ReadWriteVariables** и выбирая переменные в диалоговом окне **Выбор переменных**.  
  
 Общие сведения об использовании переменных в компоненте скрипта см. в разделе [Использование переменных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Дополнительные сведения о странице **Скрипт** в окне **Редактор преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Скрипт")](../data-flow/transformations/script-component.md).  
  
## <a name="scripting-a-source-component-in-code-design-mode"></a>Сценарная поддержка компонента источника в режиме конструктора кода  
 После настройки метаданных для компонента откройте интегрированную среду разработки средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA), чтобы написать код пользовательского скрипта. Чтобы открыть среду VSTA, щелкните **Изменить скрипт** на странице **Скрипт** окна **Редактор преобразования "скрипт"** . Можно написать скрипт на языке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# в зависимости от того, какой язык скриптов выбран в качестве значения свойства **ScriptLanguage**.  
  
 Важные сведения, относящиеся ко всем типам компонентов, создаваемым с помощью компонента скрипта, см. в разделе [Кодирование и отладка компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Основные сведения об автоматически создаваемом коде  
 При открытии интегрированной среды разработки VSTA после создания и настройки компонента источника в редакторе кода появляется класс **ScriptMain**, который можно изменять. Пользовательский код пишется в классе **ScriptMain**.  
  
 Класс **ScriptMain** содержит заглушку для метода **CreateNewOutputRows**. Метод **CreateNewOutputRows** является самым важным методом в компоненте источника.  
  
 Если открыть окно **Обозреватель проектов** в VSTA, можно увидеть, что для компонента скрипта также были созданы элементы проекта **BufferWrapper** и **ComponentWrapper**, доступные только для чтения. Класс **ScriptMain** наследуется от класса **UserComponent** в элементе проекта **ComponentWrapper**.  
  
 Во время выполнения подсистема обработки потока данных вызывает метод **PrimeOutput** в классе **UserComponent**, переопределяющий метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A> родительского класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Метод **PrimeOutput**, в свою очередь, вызывает следующие методы:  
  
1.  Метод **CreateNewOutputRows**, переопределяемый в классе **ScriptMain** для добавления строк из источника данных в выходные буферы (которые вначале пусты).  
  
2.  Метод **FinishOutputs**, который по умолчанию не содержит кода. Переопределите этот метод в классе **ScriptMain**, чтобы выполнять любую обработку, необходимую для завершения вывода.  
  
3.  Закрытый метод **MarkOutputsAsFinished**, который вызывает метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A> родительского класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> для уведомления подсистемы обработки потока данных о завершении вывода. Не следует вызывать метод **SetEndOfRowset** явно в собственном коде.  
  
### <a name="writing-your-custom-code"></a>Написание пользовательского кода  
 Чтобы завершить создание пользовательского компонента источника, может потребоваться написать скрипт в указанных ниже методах, доступных в классе **ScriptMain**.  
  
1.  Переопределите метод **AcquireConnections** для соединения с внешним источником данных. Извлеките из диспетчера соединений объект соединения или необходимые сведения о соединении.  
  
2.  Переопределите метод **PreExecute** для загрузки данных, если можно загрузить все исходные данные одновременно. Например, можно выполнить метод **SqlCommand** для соединения [!INCLUDE[vstecado](../../includes/vstecado-md.md)] с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и загрузить все исходные данные одновременно в объект **SqlDataReader**. Если требуется загружать исходные данные в виде отдельных строк (например, при чтении текстового файла), то можно загружать данные в цикле по строкам в методе **CreateNewOutputRows**.  
  
3.  Используйте переопределенный метод **CreateNewOutputRows**, чтобы добавлять новые строки в пустые выходные буферы и заполнять новые выходные строки значениями каждого столбца. Используйте метод **AddRow** каждого выходного буфера, чтобы добавить новую пустую строку, а затем задавайте значения каждого столбца. Обычно значения копируются из столбцов, загруженных из внешнего источника.  
  
4.  Переопределите метод **PostExecute**, чтобы завершить обработку данных. Например, можно закрыть модуль **SqlDataReader**, который использовался для загрузки данных.  
  
5.  Переопределите метод **ReleaseConnections**, если необходимо разорвать соединение с внешним источником данных.  
  
## <a name="examples"></a>Примеры  
 В приведенных ниже примерах демонстрируется пользовательский код, который необходим в классе **ScriptMain** для создания компонента источника.  
  
> [!NOTE]  
>  В этих примерах используется таблица **Person.Address** из образца базы данных **AdventureWorks**. В поток данных передаются ее первый и четвертый столбцы: **intAddressID** и **nvarchar(30)City**. Эти же данные используются в образцах источника, преобразования и назначения, приведенных в этом разделе. Для каждого примера приведены необходимые дополнительные условия и принимаемые предположения.  
  
### <a name="adonet-source-example"></a>Пример источника ADO.NET  
 В этом примере демонстрируется компонент источника, в котором применяется существующий диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] для загрузки данных из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в поток данных.  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Создайте диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)], использующий поставщик **SqlClient** для соединения с базой данных **AdventureWorks**.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве источника.  
  
3.  Откройте **редактор преобразования "Скрипт"** . На странице **Входы и выходы** измените имя выхода по умолчанию на более описательное имя, такое как **MyAddressOutput**, а также добавьте и настройте два выходных столбца: **AddressID** и **City**.  
  
    > [!NOTE]  
    >  Измените тип данных выходного столбца **City** на DT_WSTR.  
  
4.  На странице **Диспетчеры соединений** добавьте или создайте диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] и присвойте ему описательное имя, такое как **MyADONETConnection**.  
  
5.  На странице **Скрипт** нажмите кнопку **Изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скриптов и **редактор преобразования "скрипт"** .  
  
6.  Создайте и настройте компонент назначения, такой как назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или образец компонента назначения, демонстрируемый в разделе [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), который ожидает получения столбцов **AddressID** и **City**. Затем соедините компонент источника с назначением. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Можно создать целевую таблицу, выполнив команду [!INCLUDE[tsql](../../includes/tsql-md.md)] в базе данных **AdventureWorks**.  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
7.  Запустите образец.  
  
    ```vb  
    Imports System.Data.SqlClient  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim connMgr As IDTSConnectionManager100  
        Dim sqlConn As SqlConnection  
        Dim sqlReader As SqlDataReader  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            connMgr = Me.Connections.MyADONETConnection  
            sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            Dim cmd As New SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn)  
            sqlReader = cmd.ExecuteReader  
  
        End Sub  
  
        Public Overrides Sub CreateNewOutputRows()  
  
            Do While sqlReader.Read  
                With MyAddressOutputBuffer  
                    .AddRow()  
                    .AddressID = sqlReader.GetInt32(0)  
                    .City = sqlReader.GetString(1)  
                End With  
            Loop  
  
        End Sub  
  
        Public Overrides Sub PostExecute()  
  
            sqlReader.Close()  
  
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
        SqlDataReader sqlReader;  
  
        public override void AcquireConnections(object Transaction)  
        {  
            connMgr = this.Connections.MyADONETConnection;  
            sqlConn = (SqlConnection)connMgr.AcquireConnection(null);  
  
        }  
  
        public override void PreExecute()  
        {  
  
            SqlCommand cmd = new SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn);  
            sqlReader = cmd.ExecuteReader();  
  
        }  
  
        public override void CreateNewOutputRows()  
        {  
  
            while (sqlReader.Read())  
            {  
                {  
                    MyAddressOutputBuffer.AddRow();  
                    MyAddressOutputBuffer.AddressID = sqlReader.GetInt32(0);  
                    MyAddressOutputBuffer.City = sqlReader.GetString(1);  
                }  
            }  
  
        }  
  
        public override void PostExecute()  
        {  
  
            sqlReader.Close();  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            connMgr.ReleaseConnection(sqlConn);  
  
        }  
  
    }  
    ```  
  
### <a name="flat-file-source-example"></a>Пример источника «Неструктурированный файл»  
 В этом примере демонстрируется компонент источника, в котором используется существующий диспетчер соединений с неструктурированными файлами для загрузки данных из неструктурированного файла в поток данных. Исходные данные неструктурированного файла создаются при экспорте их из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Воспользуйтесь мастером импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы экспортировать таблицу **Person.Address** из образца базы данных **AdventureWorks** в неструктурированный файл с разделителями-запятыми. В этом образце используется файл с именем ExportedAddresses.txt.  
  
2.  Создайте диспетчер соединений с неструктурированными файлами, который подключается к экспортированному файлу данных.  
  
3.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве источника.  
  
4.  Откройте **редактор преобразования "Скрипт"** . На странице **Входы и выходы** измените имя выхода по умолчанию на более описательное имя, такое как **MyAddressOutput**. Добавьте и настройте два выходных столбца: **AddressID** и **City**.  
  
5.  На странице **Диспетчеры соединений** добавьте или создайте диспетчер соединений с неструктурированными файлами, используя описательное имя, такое как **MyFlatFileSrcConnectionManager**.  
  
6.  На странице **Скрипт** нажмите кнопку **Изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скриптов и **редактор преобразования "скрипт"** .  
  
7.  Создайте и настройте компонент назначения, такой как компонент назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или образец компонента назначения, демонстрируемый в разделе [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Затем соедините компонент источника с назначением. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Можно создать целевую таблицу, выполнив команду [!INCLUDE[tsql](../../includes/tsql-md.md)] в базе данных **AdventureWorks**.  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  Запустите образец.  
  
    ```vb  
    Imports System.IO  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Private textReader As StreamReader  
        Private exportedAddressFile As String  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connMgr As IDTSConnectionManager100 = _  
                Me.Connections.MyFlatFileSrcConnectionManager  
            exportedAddressFile = _  
                CType(connMgr.AcquireConnection(Nothing), String)  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
            MyBase.PreExecute()  
            textReader = New StreamReader(exportedAddressFile)  
        End Sub  
  
        Public Overrides Sub CreateNewOutputRows()  
  
            Dim nextLine As String  
            Dim columns As String()  
  
            Dim delimiters As Char()  
            delimiters = ",".ToCharArray  
  
            nextLine = textReader.ReadLine  
            Do While nextLine IsNot Nothing  
                columns = nextLine.Split(delimiters)  
                With MyAddressOutputBuffer  
                    .AddRow()  
                    .AddressID = columns(0)  
                    .City = columns(3)  
                End With  
                nextLine = textReader.ReadLine  
            Loop  
  
        End Sub  
  
        Public Overrides Sub PostExecute()  
            MyBase.PostExecute()  
            textReader.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.IO;  
    public class ScriptMain:  
        UserComponent  
  
    {  
        private StreamReader textReader;  
        private string exportedAddressFile;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileSrcConnectionManager;  
            exportedAddressFile = (string)connMgr.AcquireConnection(null);  
  
        }  
  
        public override void PreExecute()  
        {  
            base.PreExecute();  
            textReader = new StreamReader(exportedAddressFile);  
        }  
  
        public override void CreateNewOutputRows()  
        {  
  
            string nextLine;  
            string[] columns;  
  
            char[] delimiters;  
            delimiters = ",".ToCharArray();  
  
            nextLine = textReader.ReadLine();  
            while (nextLine != null)  
            {  
                columns = nextLine.Split(delimiters);  
                {  
                    MyAddressOutputBuffer.AddRow();  
                    MyAddressOutputBuffer.AddressID = columns[0];  
                    MyAddressOutputBuffer.City = columns[3];  
                }  
                nextLine = textReader.ReadLine();  
            }  
  
        }  
  
        public override void PostExecute()  
        {  
  
            base.PostExecute();  
            textReader.Close();  
  
        }  
  
    }  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)   
 [Разработка пользовательского компонента источника](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
  

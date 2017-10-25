---
title: "Создание источника с помощью компонента скрипта | Документы Microsoft"
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
- Script component [Integration Services], source components
- output columns [Integration Services]
- sources [Integration Services], components
ms.assetid: 547c4179-ea82-4265-8c6f-04a2aa77a3c0
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4944c3d5752da21fed90f16a38a33b4fad41515
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-source-with-the-script-component"></a>Создание источника с помощью компонента скрипта
  Компонент источника в потоке данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно использовать для загрузки данных из источника данных для передачи в нижележащие преобразования и назначения. Обычно подключение к источнику данных осуществляется через существующий диспетчер соединений.  
  
 Обзор компонента скрипта см. в разделе [расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Компонент скрипта и формируемый им код инфраструктуры значительно упрощают процесс создания пользовательских компонентов потока данных. Однако, чтобы понять работу этого компонента скрипта, может потребоваться ознакомиться с шагами, связанными с разработкой пользовательского компонента потока данных. См. в разделе [разработки компонента потока данных пользовательского](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), особенно подраздел [разработке пользовательского компонента источника](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).  
  
## <a name="getting-started-with-a-source-component"></a>Приступая к работе с компонентом источника  
 При добавлении компонента скрипта в область потока данных [!INCLUDE[ssIS](../../includes/ssis-md.md)] конструкторе **Выбор типа компонента скрипта** диалоговое окно, вам будет предложено выбрать скрипт источника, назначения или преобразования. В этом диалоговом окне выберите **источника**.  
  
## <a name="configuring-a-source-component-in-metadata-design-mode"></a>Настройка компонента источника в режиме конструктора метаданных  
 После выбора для создания компонента источника, настроить компонент с помощью **редактор преобразования «скрипт»**. Дополнительные сведения см. в разделе [Настройка компонента скрипта в редакторе компонентов скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Компонент источника потока данных не имеет входов и поддерживает один или несколько выходов. Настройка выходов для компонента является одним из шагов, которые необходимо выполнить в режиме конструктора метаданных с помощью **редактор преобразования «скрипт»**, прежде чем писать пользовательский скрипт.  
  
 Можно также указать язык скриптов, задав **ScriptLanguage** свойство **сценарий** страница **редактор преобразования «скрипт»**.  
  
> [!NOTE]  
>  Чтобы задать язык сценариев по умолчанию для компонентов скрипта и задач «скрипт», используйте **язык сценариев** параметр **Общие** страница **параметры** диалоговое окно. Дополнительные сведения см. в разделе [General Page](~/integration-services/control-flow/script-task-editor-general-page.md).  
  
### <a name="adding-connection-managers"></a>Добавление диспетчеров соединений  
 Как правило, в компоненте источника используется существующий диспетчер соединений для подключения к источнику данных, из которого загружаются данные в поток данных. На **диспетчеры соединений** страница **редактор преобразования «скрипт»**, нажмите кнопку **добавить** добавить нужный диспетчер соединений.  
  
 Но диспетчер соединений представляет собой всего лишь удобный модуль, который инкапсулирует и хранит информацию, необходимую для подключения к источнику данных конкретного типа. Чтобы загрузить или сохранить конкретные данные, необходимо написать собственный пользовательский код, а также, возможно, открыть и закрыть соединение с источником данных.  
  
 Общие сведения об использовании диспетчеров соединений в компоненте скрипта см. в разделе [соединения с источниками данных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
 Дополнительные сведения о **диспетчеры соединений** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; Страница «Диспетчеры соединений» &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-outputs-and-output-columns"></a>Настройка выходов и выходных столбцов  
 Компонент источника не имеет входов и поддерживает один или несколько выходов. На **входы и выходы** страница **редактор преобразования «скрипт»**, по умолчанию будет создан один выход, но выходные столбцы не были созданы. На этой странице редактора может понадобиться настроить следующие элементы.  
  
-   Необходимо вручную добавить и настроить выходные столбцы для каждого выхода. Выберите папку выходные столбцы для каждого выхода, а затем использовать **добавить столбец** и **удалить столбец** кнопки, чтобы управлять выходными столбцами для каждого выхода компонента источника. В дальнейшем можно будет ссылаться на выходные столбцы в скрипте по именам, присвоенным здесь, используя свойства типизированного метода доступа, созданные в автоматически сформированном коде.  
  
-   Может потребоваться создать один или несколько дополнительных выводов, таких как эмулируемый вывод ошибок для строк, содержащих непредвиденные значения. Используйте **Добавить выходные данные** и **удалить Выход** кнопки для управления выходами компонента источника. Все входные строки направляются во все доступные выходы, если не выбирается идентичные ненулевое значение для **ExclusionGroup** свойства тех выходов, где планируется направить каждую строку только один из выходов, одного и того же **ExclusionGroup** значение. Конкретное целочисленное значение, выбранное для идентификации **ExclusionGroup** не имеет значения.  
  
    > [!NOTE]  
    >  Можно также использовать ненулевое значение **ExclusionGroup** значение свойства с единственным выходом, если не требуется выводить все строки. Таким образом, тем не менее, необходимо явно вызвать **DirectRowTo\<outputbuffer >** метод для каждой строки, которую требуется отправить в выход.  
  
-   Может потребоваться присвоить выходам понятные имена. В дальнейшем можно будет ссылаться на выходы по их именам в скрипте, используя свойства типизированного метода доступа, созданные в автоматически сформированном коде.  
  
-   Обычно несколько выходов в одной **ExclusionGroup** имеют одинаковые выходные столбцы. Однако, если создается моделируемый вывод ошибок, может потребоваться добавить дополнительные столбцы для хранения сведений об ошибках. Сведения о том, как подсистема обработки потока данных обрабатывает ошибочные строки, см. в разделе [с помощью вывода ошибок в компоненте потока данных](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md). Тем не менее в компоненте скрипта необходимо написать собственный код, чтобы заполнить дополнительные столбцы соответствующими сведениями об ошибках. Дополнительные сведения см. в разделе [имитация вывода ошибок для компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Дополнительные сведения о **входы и выходы** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; входов и выходов страницу &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Добавление переменных  
 При наличии существующих переменных, значения которых вы хотите использовать в скрипте, можно добавить их в **ReadOnlyVariables** и **ReadWriteVariables** поля свойств на **сценария** страница **редактор преобразования «скрипт»**.  
  
 При вводе нескольких переменных в поля свойств разделяйте имена переменных запятыми. Также можно ввести несколько переменных, нажав кнопку с многоточием (**...** ) рядом с **ReadOnlyVariables** и **ReadWriteVariables** поля свойств и выбирая переменные в **Выбор переменных** диалоговое окно .  
  
 Общие сведения об использовании переменных в компоненте скрипта см. в разделе [использование переменных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Дополнительные сведения о **сценарий** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; Страница «скрипт» &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-source-component-in-code-design-mode"></a>Сценарная поддержка компонента источника в режиме конструктора кода  
 После настройки метаданных для компонента откройте [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA) IDE, чтобы код пользовательского скрипта. Чтобы открыть среду VSTA, щелкните **изменить скрипт** на **сценарий** страница **редактор преобразования «скрипт»**. Можно написать скрипт с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#, в зависимости от языка скрипта, выбранного для **ScriptLanguage** свойство.  
  
 Важные сведения, относящиеся ко всем типам компонентов, созданных с помощью компонента скрипта см. в разделе [кодировании и отладке компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Основные сведения об автоматически создаваемом коде  
 При открытии интегрированной среды разработки VSTA после создания и настройки компонента источника, редактируемый **ScriptMain** класс появится в редакторе кода. Написать пользовательский код **ScriptMain** класса.  
  
 **ScriptMain** класс включает заглушку для **CreateNewOutputRows** метод. **CreateNewOutputRows** является наиболее важным методом в компоненте источника.  
  
 При открытии **обозревателя проектов** окна в VSTA, можно увидеть, что компонент скрипта также создал только для чтения **BufferWrapper** и **ComponentWrapper** проекта элементы. **ScriptMain** класс наследует от **UserComponent** класса в **ComponentWrapper** элемент проекта.  
  
 Во время выполнения подсистема обработки потока данных вызывает **PrimeOutput** метод в **UserComponent** класс, переопределяющий <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A> метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> родительского класса. **PrimeOutput** метод в свою очередь вызывает следующие методы:  
  
1.  **CreateNewOutputRows** метод, который можно переопределить в **ScriptMain** для добавления строк из источника данных к выходу вначале пусты буферов, которые являются.  
  
2.  **FinishOutputs** метод, который по умолчанию пусто. Переопределите этот метод в **ScriptMain** для выполнения обработки, необходимое для завершения вывода.  
  
3.  Закрытый **MarkOutputsAsFinished** метод, который вызывает <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A> метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> родительского класса для указания подсистемы обработки потока данных, выходных данных завершена. Нет необходимости вызывать **SetEndOfRowset** явно в собственном коде.  
  
### <a name="writing-your-custom-code"></a>Написание пользовательского кода  
 Чтобы завершить создание пользовательского компонента источника, может потребоваться написать скрипт в следующие методы, доступные в **ScriptMain** класса.  
  
1.  Переопределить **AcquireConnections** способ подключения к внешнему источнику данных. Извлеките из диспетчера соединений объект соединения или необходимые сведения о соединении.  
  
2.  Переопределить **PreExecute** метод для загрузки данных, если можно загрузить все исходные данные одновременно. Например, можно выполнить **SqlCommand** от [!INCLUDE[vstecado](../../includes/vstecado-md.md)] соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных и загрузить все исходные данные одновременно в **SqlDataReader**. Если необходимо загрузить одну строку источника данных во время (например, при чтении текстового файла), можно загрузить данные в цикле по строкам в **CreateNewOutputRows**.  
  
3.  Используйте переопределенный **CreateNewOutputRows** метод, чтобы добавлять новые строки в пустые выходные буфера и заполнять значения каждого столбца в новые строки вывода. Используйте **метода AddRow** метод каждого выходного буфера, чтобы добавить новую пустую строку и затем задавайте значения каждого столбца. Обычно значения копируются из столбцов, загруженных из внешнего источника.  
  
4.  Переопределить **PostExecute** метод, чтобы завершить обработку данных. Например, можно закрыть **SqlDataReader** вы использовали для загрузки данных.  
  
5.  Переопределить **ReleaseConnections** метод для отключения от внешнего источника данных, если это необходимо.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется пользовательский код, который является обязательным в **ScriptMain** класса для создания компонента источника.  
  
> [!NOTE]  
>  В этих примерах используются **Person.Address** в таблицу **AdventureWorks** образца базы данных и передается ее первый и четвертый столбец **intAddressID** и  **Город nvarchar (30)** поток данных. Эти же данные используются в образцах источника, преобразования и назначения, приведенных в этом разделе. Для каждого примера приведены необходимые дополнительные условия и принимаемые предположения.  
  
### <a name="adonet-source-example"></a>Пример источника ADO.NET  
 В этом примере демонстрируется компонент источника, пользующихся существующими [!INCLUDE[vstecado](../../includes/vstecado-md.md)] диспетчер соединений для загрузки данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы в поток данных.  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Создание [!INCLUDE[vstecado](../../includes/vstecado-md.md)] диспетчер соединений, который использует **SqlClient** поставщик для подключения к **AdventureWorks** базы данных.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве источника.  
  
3.  Откройте **редактор преобразования «скрипт»**. На **входы и выходы** страницы, такие как выхода на более описательное имя по умолчанию **MyAddressOutput**и добавьте и настройте два выходных столбца, **AddressID**и **Город**.  
  
    > [!NOTE]  
    >  Не забудьте изменить тип данных **Город** выходного столбца к типу данных DT_WSTR.  
  
4.  На **диспетчеры соединений** добавьте или создайте [!INCLUDE[vstecado](../../includes/vstecado-md.md)] диспетчер соединений и присвойте ему имя, например **соединение Adonet**.  
  
5.  На **сценарий** щелкните **изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скриптов и **редактор преобразования «скрипт»**.  
  
6.  Создайте и настройте компонент назначения, такие как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения или образец компонента назначения, демонстрируемый в [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), который ожидает  **AddressID** и **Город** столбцов. Затем соедините компонент источника с назначением. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Можно создать целевую таблицу, выполнив следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] в **AdventureWorks** базы данных:  
  
    ```  
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
  
1.  Используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта для экспорта **Person.Address** таблицу **AdventureWorks** образца базы данных в неструктурированный файл с разделителями запятыми. В этом образце используется файл с именем ExportedAddresses.txt.  
  
2.  Создайте диспетчер соединений с неструктурированными файлами, который подключается к экспортированному файлу данных.  
  
3.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве источника.  
  
4.  Откройте **редактор преобразования «скрипт»**. На **входы и выходы** страницы, такие как выхода на более описательное имя по умолчанию **MyAddressOutput**. Добавьте и настройте два выходных столбца, **AddressID** и **Город**.  
  
5.  На **диспетчеры соединений** добавьте или создайте соединения с неструктурированным файлом диспетчер, используя описательное имя, например **«диспетчерсоединенийснеструктурированнымфайлом»**.  
  
6.  На **сценарий** щелкните **изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скриптов и **редактор преобразования «скрипт»**.  
  
7.  Создайте и настройте компонент назначения, такие как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения или образец компонента назначения, демонстрируемый в [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Затем соедините компонент источника с назначением. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Можно создать целевую таблицу, выполнив следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] в **AdventureWorks** базы данных:  
  
    ```  
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
  
  


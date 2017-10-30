---
title: "Создание асинхронного преобразования с помощью компонента скрипта | Документы Microsoft"
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
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4da61e00337430a3eaef84e40f9f732a572cc45b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a>Создание асинхронного преобразования с помощью компонента скрипта
  Компонент преобразования используется в потоке данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для изменения и анализа данных, передаваемых из источника в назначение. Преобразование с синхронными выходами обрабатывает каждую входную строку, проходящую через компонент. Преобразование с асинхронным выходом может ожидать завершения его обработки, пока не получит все входные строки, или может отправить на выход определенные строки до получения всех входных строк. В данном разделе описано асинхронное преобразование. Если требуется синхронное преобразование, в разделе [создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md). Дополнительные сведения о различиях между синхронными и асинхронными выходами см. в разделе [основные сведения о синхронных и асинхронных преобразованиях](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Обзор компонента скрипта см. в разделе [расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Компонент скрипта и автоматически создаваемый инфраструктурный код упрощают процесс разработки пользовательских компонентов потока данных. Тем не менее, чтобы понять, как работает компонент скрипта, вам может быть полезно ознакомиться с шагами, которые необходимо выполнить при разработке пользовательского компонента потока данных в [разработке пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) раздела, и особенно [Разработка пользовательского компонента преобразования с синхронными выходами](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
## <a name="getting-started-with-an-asynchronous-transformation-component"></a>Приступая к работе с компонентом асинхронного преобразования  
 При добавлении компонента скрипта на вкладку «поток данных» [!INCLUDE[ssIS](../../includes/ssis-md.md)] конструкторе **Выбор типа компонента скрипта** появляется диалоговое окно с приглашением настроить компонент как источник, преобразование или назначение. В этом диалоговом окне выберите **преобразования**.  
  
## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a>Настройка компонента асинхронного преобразования в режиме конструктора метаданных  
 После выбора параметра для создания компонента преобразования, настроить компонент с помощью **редактор преобразования «скрипт»**. Дополнительные сведения см. в разделе [Настройка компонента скрипта в редакторе компонентов скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Выберите язык сценария, который будет использовать компонент скрипта, задайте **ScriptLanguage** свойство **сценарий** страница **редактор преобразования «скрипт»** диалоговое окно поле.  
  
> [!NOTE]  
>  Чтобы задать значение по умолчанию языка скрипта для компонента скрипта, используйте **язык сценариев** параметр **Общие** страница **параметры** диалоговое окно. Дополнительные сведения см. в разделе [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Компонент преобразования потока данных имеет один вход и поддерживает один или несколько выходов. Настройка входа и выходов компонента является одним из шагов, которые необходимо выполнить в режиме конструктора метаданных с помощью **редактор преобразования «скрипт»**, прежде чем писать пользовательский скрипт.  
  
### <a name="configuring-input-columns"></a>Настройка входных столбцов  
 Компонент преобразования, созданный с помощью компонента скрипта, имеет только один выход.  
  
 На **входные столбцы** страница **редактор преобразования «скрипт»**, в списке показаны доступные столбцы из выходных данных вышестоящего компонента потока данных. Выделите столбцы, которые хотите преобразовать или передать. Пометьте все столбцы, участвующие в преобразовании, как доступные для чтения и записи.  
  
 Дополнительные сведения о **входные столбцы** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; страницы столбцы входных данных &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>Настройка входов, выходов и выходных столбцов  
 Компонент преобразования поддерживает один или несколько выходов.  
  
 Часто преобразование с асинхронным выходом имеет два выхода. Например, при подсчете количества адресов в указанном городе может потребоваться отправить данные об адресах через один выход, а результаты статистической обработки — через другой. Выход статистической обработки также требует нового выходного столбца.  
  
 На **входы и выходы** страница **редактор преобразования «скрипт»**, вы видите, что по умолчанию будет создан один выход, но выходные столбцы не были созданы. На этой странице редактора можно настроить следующие элементы.  
  
-   Можно создать один или несколько дополнительных выходов, например выход для результата статистической обработки. Используйте **Добавить выходные данные** и **удалить Выход** кнопки для управления выходами компонент асинхронного преобразования. Задать **SynchronousInputID** свойства для каждого выхода значение 0, чтобы указать, что выходные данные не просто передает данные из вышестоящего компонента или преобразует их на месте в существующих строках и столбцах. Именно этот параметр делает выходы асинхронными по отношению к входу.  
  
-   Входу и выходам можно назначить понятные имена. Компонент скрипта использует эти имена для создания типизированных свойств метода доступа, с помощью которых в скрипте выполняется обращение к входам и выходам.  
  
-   Часто при асинхронном преобразовании к потоку данных добавляются столбцы. Когда **SynchronousInputID** выхода равно нулю, указывающее, что выходные данные не просто передает данные из вышестоящего компонента или преобразует их на месте в существующих строках и столбцах, необходимо добавить и настроить выходные столбцы явным образом на выходе. Выходные столбцы не обязательно должны имеет такие же имена, как входные столбцы, с которыми они сопоставляются.  
  
-   Можно добавить дополнительные столбцы для дополнительной информации. Чтобы дополнительные столбцы заполнялись данными, необходимо написать собственный код. Сведения о воспроизведении поведения стандартного вывода ошибок см. в разделе [имитация вывода ошибок для компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Дополнительные сведения о **входы и выходы** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; входов и выходов страницу &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Добавление переменных  
 При наличии существующих переменных, значения которых вы хотите использовать в скрипте, можно добавить их в поле свойства ReadOnlyVariables и ReadWriteVariables на **сценарий** страница **редактор преобразования «скрипт»** .  
  
 Если в поле свойства добавляются несколько переменных, их имена нужно разделять запятыми. Можно также выбрать несколько переменных, нажав кнопку с многоточием (**...** ) рядом с **ReadOnlyVariables** и **ReadWriteVariables** поля свойств, а затем выбрав переменные в **Выбор переменных** диалоговое окно.  
  
 Общие сведения об использовании переменных в компоненте скрипта см. в разделе [использование переменных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Дополнительные сведения о **сценарий** страница **редактор преобразования «скрипт»**, в разделе [редактор преобразования «скрипт» &#40; Страница «скрипт» &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a>Создание скрипта компонента асинхронного преобразования в режиме конструктора кода  
 После настройки всех метаданных компонента можно написать пользовательский скрипт. В **редактор преобразования «скрипт»**на **сценарий** щелкните **изменить скрипт** Открытие [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA) интегрированной среды разработки где можно добавить пользовательский скрипт. Язык сценариев, который вы используете зависит от того, можно выбрать [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# как язык скриптов для **ScriptLanguage** свойство **сценария** страница.  
  
 Важные сведения, относящиеся ко всем типам компонентов, созданных с помощью компонента скрипта см. в разделе [кодировании и отладке компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Основные сведения об автоматически создаваемом коде  
 При открытии интегрированной среды разработки VSTA после создания и настройки компонента преобразования, редактируемый **ScriptMain** класс появится в редакторе кода с заглушками ProcessInputRow и CreateNewOutputRows методы. Класс ScriptMain — где написании пользовательского кода, а ProcessInputRow — наиболее важным методом в компоненте преобразования. **CreateNewOutputRows** метод обычно используется в компоненте источника, который похож на асинхронное преобразование, в том, что оба компонента должны создавать собственные выходные строки.  
  
 При открытии VSTA **обозревателя проектов** окна, можно увидеть, что компонент скрипта также создал только для чтения **BufferWrapper** и **ComponentWrapper** элементы проекта . ScriptMain класс наследуется от класса UserComponent **ComponentWrapper** элемент проекта.  
  
 Во время выполнения подсистема обработки потока данных вызывает метод PrimeOutput в **UserComponent** класс, переопределяющий <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A> метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> родительского класса. Метод PrimeOutput, в свою очередь, вызывает метод CreateNewOutputRows.  
  
 Затем подсистема обработки потока данных вызывает метод ProcessInput в класс UserComponent, который переопределяет <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> родительского класса. Метод ProcessInput в свою очередь просматривает строки во входном буфере и вызывает метод ProcessInputRow один раз для каждой строки.  
  
### <a name="writing-your-custom-code"></a>Написание пользовательского кода  
 Чтобы завершить создание пользовательского компонента асинхронного преобразования, необходимо использовать переопределенный метод ProcessInputRow для обработки данных в каждой строке входного буфера. Поскольку выходы асинхронны по отношению к входу, необходимо явно указать строки данных для выходов.  
  
 При асинхронном преобразовании метода AddRow можно использовать для добавления строк к выходу по мере необходимости из методов ProcessInputRow или ProcessInput. Необходимо использовать метод CreateNewOutputRows. При создании одной строки результатов, например результатов статистической обработки в определенный выход можно создать выходную строку заранее с помощью метода CreateNewOutputRows и заполнить ее значениями позже, после обработки всех входных строк. Однако не полезны для создания нескольких строк в методе CreateNewOutputRows, так как компонент скрипта позволяет использовать только текущей строки входных или выходных данных. Метод CreateNewOutputRows более важен в компоненте источника там, где нет входных строк для обработки.  
  
 Можно также переопределить метод ProcessInput, которая может выполнять дополнительную предварительную или финальную обработку перед или после перебор входного буфера и вызовите ProcessInputRow для каждой строки. Например, один из примеров кода в этом разделе переопределения ProcessInput для подсчета количества адресов в определенном городе как ProcessInputRow обрабатывает в цикле строки**.** Суммарное значение записывается на второй Выход после обработки всех строк. Пример завершения выходные данные в ProcessInput, поскольку выходные буферы недоступны при вызове PostExecute.  
  
 В зависимости от требований можно также написать скрипт в PreExecute и PostExecute методов, доступных в классе ScriptMain, чтобы выполнить предварительную или итоговую обработку.  
  
> [!NOTE]  
>  При разработке пользовательского компонента потока данных с нуля, было бы важно переопределить метод PrimeOutput для кэширования ссылок на выходные буферы, чтобы можно было добавлять строки данных в буферы позднее. В компоненте скрипта это не требуется, так как у вас есть автоматически создаваемый класс, представляющий каждый выходной буфер в **BufferWrapper** элемент проекта.  
  
## <a name="example"></a>Пример  
 В этом примере демонстрируется пользовательский код, который необходим в классе ScriptMain для создания компонента асинхронного преобразования.  
  
> [!NOTE]  
>  В этих примерах используются **Person.Address** в таблицу **AdventureWorks** образца базы данных и передается ее первый и четвертый столбец **intAddressID** и  **Город nvarchar (30)** поток данных. Эти же данные используются в образцах источника, преобразования и назначения, приведенных в этом разделе. Для каждого примера приведены необходимые дополнительные условия и принимаемые предположения.  
  
 В данном примере показан компонент асинхронного преобразования с двумя выходами. Это преобразование передает **AddressID** и **Город** столбцы один выход, пока оно подсчитывает количество адресов в определенном городе (Редмонд, штат Вашингтон, США), а затем выходные данные результирующее значение на второй выход.  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования.  
  
2.  Подсоедините в конструкторе выход источника или другого преобразования к новому компоненту преобразования. Этот вывод должен предоставлять данные из **Person.Address** таблицу **AdventureWorks** образца базы данных, который содержит по крайней мере **AddressID** и  **Город** столбцов.  
  
3.  Откройте **редактор преобразования «скрипт»**. На **входные столбцы** выберите **AddressID** и **Город** столбцов.  
  
4.  На **входы и выходы** добавьте и настройте **AddressID** и **Город** выходные столбцы для первого выхода. Добавьте второй выход и добавьте выходной столбец для суммарного значения на втором выходе. Задайте для свойства SynchronousInputID первого выхода значение 0, так как в этом примере каждая входящая строка явно копируется на первый выход. Для свойства SynchronousInputID созданного выхода уже задано значение 0.  
  
5.  Переименуйте вход, выходы и новый выходной столбец, присвоив им более понятные имена. В этом примере **MyAddressInput** как имя входа, **MyAddressOutput** и **MySummaryOutput** для выходов и **MyRedmondCount** для выходного столбца на втором выходе.  
  
6.  На **сценарий** щелкните **изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скриптов и **редактор преобразования «скрипт»**.  
  
7.  Создайте и настройте компонент назначения для первого выхода, ожидающего **AddressID** и **Город** столбцы, такие как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения или образец компонента назначения показанные в [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md),. Затем подсоедините первый выход преобразования, **MyAddressOutput**, к компоненту назначения. Можно создать целевую таблицу, выполнив следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] в **AdventureWorks** базы данных:  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  Создайте и настройте другой компонент назначения для второго выхода. Затем Подсоедините второй выход преобразования, **MySummaryOutput**, к компоненту назначения. Поскольку второй выход записывает только одну строку с одним значением, можно легко настроить компонент назначения с помощью диспетчера соединений с неструктурированными файлами, подключающегося к новому файлу с единственным столбцом. В примере этот целевой столбец называется **MyRedmondCount**.  
  
9. Запустите образец.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Private myRedmondAddressCount As Integer  
  
    Public Overrides Sub CreateNewOutputRows()  
  
        MySummaryOutputBuffer.AddRow()  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)  
  
        While Buffer.NextRow()  
            MyAddressInput_ProcessInputRow(Buffer)  
        End While  
  
        If Buffer.EndOfRowset Then  
            MyAddressOutputBuffer.SetEndOfRowset()  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount  
            MySummaryOutputBuffer.SetEndOfRowset()  
        End If  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With MyAddressOutputBuffer  
            .AddRow()  
            .AddressID = Row.AddressID  
            .City = Row.City  
        End With  
  
        If Row.City.ToUpper = "REDMOND" Then  
            myRedmondAddressCount += 1  
        End If  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
{  
    private int myRedmondAddressCount;  
  
    public override void CreateNewOutputRows()  
    {  
  
        MySummaryOutputBuffer.AddRow();  
  
    }  
  
    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)  
    {  
  
        while (Buffer.NextRow())  
        {  
            MyAddressInput_ProcessInputRow(Buffer);  
        }  
  
        if (Buffer.EndOfRowset())  
        {  
            MyAddressOutputBuffer.SetEndOfRowset();  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;  
            MySummaryOutputBuffer.SetEndOfRowset();  
        }  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            MyAddressOutputBuffer.AddRow();  
            MyAddressOutputBuffer.AddressID = Row.AddressID;  
            MyAddressOutputBuffer.City = Row.City;  
        }  
  
        if (Row.City.ToUpper() == "REDMOND")  
        {  
            myRedmondAddressCount += 1;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о синхронных и асинхронных преобразованиях](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
 [Разработка пользовательского компонента преобразования с асинхронными выходами](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
  
  


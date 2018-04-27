---
title: Создание асинхронного преобразования с помощью компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: extending-packages-scripting-data-flow-script-component-types
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c7a8ecd16aa8ea4957b54195feb66b3b8824d6b1
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a>Создание асинхронного преобразования с помощью компонента скрипта
  Компонент преобразования используется в потоке данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для изменения и анализа данных, передаваемых из источника в назначение. Преобразование с синхронными выходами обрабатывает каждую входную строку, проходящую через компонент. Преобразование с асинхронным выводом может ожидать завершения обработки, пока не получит все входные строки, или может вывести определенные строки до получения всех входных строк. В данном разделе описано асинхронное преобразование. Если для обработки требуется синхронное преобразование, см. раздел [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md). Дополнительные сведения о различиях между синхронными и асинхронными компонентами см. в разделе [Основные сведения о синхронных и асинхронных преобразованиях](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Общие сведения о компоненте скрипта см. в разделе [Расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Компонент скрипта и автоматически создаваемый инфраструктурный код упрощают процесс разработки пользовательских компонентов потока данных. Однако, чтобы понять, как работает компонент скрипта, может быть полезно ознакомиться с шагами по разработке пользовательских компонентов потока данных, описанными в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) и в особенности в разделе [Разработка пользовательского компонента преобразования с синхронными выходами](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
## <a name="getting-started-with-an-asynchronous-transformation-component"></a>Приступая к работе с компонентом асинхронного преобразования  
 При добавлении компонента скрипта на вкладке "Поток данных" конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] открывается диалоговое окно **Выбор типа компонента скрипта** с приглашением настроить компонент в качестве источника, преобразования или назначения. В этом диалоговом окне выберите пункт **Преобразование**.  
  
## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a>Настройка компонента асинхронного преобразования в режиме конструктора метаданных  
 После выбора варианта для создания компонента преобразования выполняется настройка компонента с помощью **редактора преобразования "Скрипт"**. Дополнительные сведения см. в разделе [Настройка компонента скрипта в редакторе компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Чтобы выбрать язык скрипта в компоненте скрипта, нужно задать свойство **ScriptLanguage** на странице **Скрипт** диалогового окна **Редактор преобразования "скрипт"**.  
  
> [!NOTE]  
>  Чтобы установить язык скрипта по умолчанию для компонента скрипта, воспользуйтесь параметром **Язык сценариев** на странице **Общие** диалогового окна **Параметры**. Дополнительные сведения см. в разделе [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Компонент преобразования потока данных имеет один вход и поддерживает один или несколько выходов. Настройка входа и выходов компонента — это один из шагов, которые необходимо выполнить в режиме конструктора метаданных с помощью **редактора преобразования "скрипт"**, прежде чем писать пользовательский скрипт.  
  
### <a name="configuring-input-columns"></a>Настройка входных столбцов  
 Компонент преобразования, созданный с помощью компонента скрипта, имеет только один выход.  
  
 На странице **Входные столбцы** в окне **Редактор преобразования "скрипт"** в списке показаны доступные столбцы из выходных данных вышестоящего компонента в потоке данных. Выделите столбцы, которые хотите преобразовать или передать. Пометьте все столбцы, участвующие в преобразовании, как доступные для чтения и записи.  
  
 Дополнительные сведения о странице **Входные столбцы** **редактора преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Входные столбцы")](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>Настройка входов, выходов и выходных столбцов  
 Компонент преобразования поддерживает один или несколько выходов.  
  
 Часто преобразование с асинхронным выходом имеет два выхода. Например, при подсчете количества адресов в указанном городе может потребоваться отправить данные об адресах через один выход, а результаты статистической обработки — через другой. Выход статистической обработки также требует нового выходного столбца.  
  
 На странице **Входы и выходы** в окне **Редактор преобразования "скрипт"** видно, что по умолчанию создан один выход, но не созданы выходные столбцы. На этой странице редактора можно настроить следующие элементы.  
  
-   Можно создать один или несколько дополнительных выходов, например выход для результата статистической обработки. Для управления выходами компонента асинхронного преобразования пользуйтесь кнопками **Добавить выход** и **Удалить выход**. Задайте для свойства **SynchronousInputID** каждого выхода значение 0, что указывает, что выход не просто передает данные из вышестоящего компонента или преобразует их на месте в существующих строках и столбцах. Именно этот параметр делает выходы асинхронными по отношению к входу.  
  
-   Входу и выходам можно назначить понятные имена. Компонент скрипта использует эти имена для создания типизированных свойств метода доступа, с помощью которых в скрипте выполняется обращение к входам и выходам.  
  
-   Часто при асинхронном преобразовании к потоку данных добавляются столбцы. Если для свойства **SynchronousInputID** выхода задано значение 0, указывающее, что выход не просто передает данные из вышестоящего компонента или преобразует их на месте в существующих строках и столбцах, то для выхода необходимо явно добавить и настроить выходные столбцы. Выходные столбцы не обязательно должны имеет такие же имена, как входные столбцы, с которыми они сопоставляются.  
  
-   Можно добавить дополнительные столбцы для дополнительной информации. Чтобы дополнительные столбцы заполнялись данными, необходимо написать собственный код. Сведения о воспроизведении поведения стандартного вывода ошибок см. в разделе [Имитация вывода ошибок для компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Дополнительные сведения о странице **Входы и выходы** **редактора преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Входы и выходы")](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Добавление переменных  
 Если нужно использовать в скрипте значения существующих переменных, их можно добавить в поля свойств ReadOnlyVariables и ReadWriteVariables на странице **Скрипт** в **редакторе преобразования "скрипт"**.  
  
 Если в поле свойства добавляются несколько переменных, их имена нужно разделять запятыми. Также можно выбрать несколько переменных, нажав кнопку с многоточием (**…**), расположенную рядом с полями свойств **ReadOnlyVariables** и **ReadWriteVariables**, а затем выбрав переменные в диалоговом окне **Выбор переменных**.  
  
 Общие сведения об использовании переменных в компоненте скрипта см. в разделе [Использование переменных в компоненте скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Дополнительные сведения о странице **Скрипт** в окне **Редактор преобразования "Скрипт"** см. в разделе [Редактор преобразования "Скрипт" (страница "Скрипт")](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a>Создание скрипта компонента асинхронного преобразования в режиме конструктора кода  
 После настройки всех метаданных компонента можно написать пользовательский скрипт. В **редакторе преобразования "Скрипт"** на странице **Скрипт** нажмите кнопку **Изменить скрипт**, чтобы открыть интегрированную среду разработки средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA), где можно добавить пользовательский скрипт. Используемый язык скриптов зависит от значения свойства **ScriptLanguage**, указанного на странице **Скрипт**. В качестве значения можно выбрать язык [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Важные сведения, относящиеся ко всем типам компонентов, создаваемым с помощью компонента скрипта, см. в разделе [Кодирование и отладка компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Основные сведения об автоматически создаваемом коде  
 Если открыть интегрированную среду разработки VSTA после создания и настройки компонента преобразования, в редакторе кода появляется редактируемый класс **ScriptMain** с заглушками для методов ProcessInputRow и CreateNewOutputRows. Пользовательский код создается в классе ScriptMain, а самым важным методом в компоненте преобразования является ProcessInputRow. Метод **CreateNewOutputRows** обычно используется в компоненте источника, который похож на асинхронное преобразование тем, что оба компонента должны создавать собственные выходные строки.  
  
 В окне **Обозреватель проектов** среды VSTA видно, что компонент скрипта также создал доступные только для чтения элементы проекта **BufferWrapper** и **ComponentWrapper**. Класс ScriptMain наследуется от класса UserComponent в элементе проекта **ComponentWrapper**.  
  
 Во время выполнения подсистема обработки потока данных вызывает метод PrimeOutput в классе **UserComponent**, переопределяющий метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A> родительского класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Метод PrimeOutput, в свою очередь, вызывает метод CreateNewOutputRows.  
  
 Затем подсистема обработки потоков данных вызывает метод ProcessInput в классе UserComponent, переопределяющий метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> родительского класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. В свою очередь, метод ProcessInput проходит по строкам во входном буфере и вызывает для каждой строки метод ProcessInputRow.  
  
### <a name="writing-your-custom-code"></a>Написание пользовательского кода  
 Для завершения создания пользовательского компонента асинхронного преобразования необходимо использовать переопределенный метод ProcessInputRow для обработки данных в каждой строке входного буфера. Поскольку выходы асинхронны по отношению к входу, необходимо явно указать строки данных для выходов.  
  
 При асинхронном преобразовании можно использовать метод AddRow для добавления строк к выходу по мере необходимости из методов ProcessInputRow или ProcessInput. Метод CreateNewOutputRows использовать не требуется. При записи одной строки результатов, например результатов статистической обработки, в определенный выход можно создать выходную строку заранее с помощью метода CreateNewOutputRows и заполнить ее значениями позже, после обработки всех входных строк. Однако создавать много строк в методе CreateNewOutputRows не имеет смысла, так как компонент скрипта позволяет использовать только текущую строку входных или выходных данных. Метод CreateNewOutputRows более важен в компоненте источника, где нет входных строк для обработки.  
  
 Может также потребоваться переопределить сам метод ProcessInput, чтобы можно было выполнять дополнительную предварительную или окончательную обработку перед или после циклической обработки данных из входного буфера и вызывать метод ProcessInputRow для каждой строки. Например, в одном из примеров в этом разделе метод ProcessInput переопределяется для подсчета адресов в определенном городе по мере перебора строк методом ProcessInputRow **.** Суммарное значение записывается во второй выход после обработки всех строк. В примере вывод совершается в ProcessInput, так как выходные буферы недоступны после вызова PostExecute.  
  
 В зависимости от требований можно также создать скрипт в методах PreExecute и PostExecute, доступных в классе ScriptMain для выполнения предварительной или окончательной обработки.  
  
> [!NOTE]  
>  При разработке пользовательского компонента потока данных с нуля было бы важно переопределить метод PrimeOutput для кэширования ссылок на выходные буферы, чтобы можно было добавлять строки данных в буферы позднее. В компоненте скрипта это необязательно, так как существует автоматически создаваемый класс, представляющий каждый выходной буфер в элементе проекта **BufferWrapper**.  
  
## <a name="example"></a>Пример  
 В этом примере показан пользовательский код, который требуется классу ScriptMain для создания компонента асинхронного преобразования.  
  
> [!NOTE]  
>  В этих примерах используется таблица **Person.Address** из образца базы данных **AdventureWorks**. В поток данных передаются ее первый и четвертый столбцы: **intAddressID** и **nvarchar(30)City**. Эти же данные используются в образцах источника, преобразования и назначения, приведенных в этом разделе. Для каждого примера приведены необходимые дополнительные условия и принимаемые предположения.  
  
 В данном примере показан компонент асинхронного преобразования с двумя выходами. Это преобразование передает столбцы **AddressID** и **City** в один выход и в то же время подсчитывает адреса в определенном городе (Редмонд, Вашингтон, США), а затем передает результирующее значение во второй выход.  
  
 Для запуска этого образца кода необходимо настроить пакет и компонент следующим образом.  
  
1.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования.  
  
2.  Подсоедините в конструкторе выход источника или другого преобразования к новому компоненту преобразования. Этот выход должен содержать данные из таблицы **Person.Address** образца базы данных **AdventureWorks**, которая содержит по крайней мере столбцы **AddressID** и **City**.  
  
3.  Откройте **редактор преобразования "Скрипт"**. На странице **Входные столбцы** выберите столбцы **AddressID** и **City**.  
  
4.  На странице **Входы и выходы** добавьте и настройте выходные столбцы **AddressID** и **City** для первого выхода. Добавьте второй выход и добавьте выходной столбец для суммарного значения на втором выходе. Задайте для свойства SynchronousInputID первого выхода значение 0, так как в этом примере каждая входящая строка явно копируется на первый выход. Для свойства SynchronousInputID созданного выхода уже задано значение 0.  
  
5.  Переименуйте вход, выходы и новый выходной столбец, присвоив им более понятные имена. В примере используются следующие имена: **MyAddressInput** для входа, **MyAddressOutput** и **MySummaryOutput** для выходов и **MyRedmondCount** для выходного столбца во втором выходе.  
  
6.  На странице **Скрипт** нажмите кнопку **Изменить скрипт** и введите следующий скрипт. Затем закройте среду разработки скриптов и **редактор преобразования "Скрипт"**.  
  
7.  Создайте и настройте компонент назначения для первого выхода, ожидающего столбцы **AddressID** и **City**, например назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или образец компонента назначения, показанный в разделе [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Затем подсоедините первый выход преобразования, **MyAddressOutput**, к компоненту назначения. Можно создать целевую таблицу, выполнив команду [!INCLUDE[tsql](../../includes/tsql-md.md)] в базе данных **AdventureWorks**.  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  Создайте и настройте другой компонент назначения для второго выхода. Затем подсоедините второй выход преобразования, **MySummaryOutput**, к компоненту назначения. Поскольку второй выход записывает только одну строку с одним значением, можно легко настроить компонент назначения с помощью диспетчера соединений с неструктурированными файлами, подключающегося к новому файлу с единственным столбцом. В примере этот целевой столбец называется **MyRedmondCount**.  
  
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
  
  

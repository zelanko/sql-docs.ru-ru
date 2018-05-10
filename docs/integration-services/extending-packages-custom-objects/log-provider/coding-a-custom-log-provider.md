---
title: Создание кода пользовательского регистратора | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: extending-packages-custom-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom log providers [Integration Services], coding
ms.assetid: 979a29ca-956e-4fdd-ab47-f06e84cead7a
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a40454dd0095541bd0b714eaa93a1d296aacdb30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="coding-a-custom-log-provider"></a>Создание кода пользовательского регистратора
  После создания класса, наследующего от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, и применения к нему атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>, необходимо переопределить реализацию свойств и методов базового класса, чтобы обеспечить пользовательские функциональные возможности.  
  
 Примеры пользовательских регистраторов см. в разделе [Разработка пользовательского интерфейса для пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-user-interface-for-a-custom-log-provider.md).  
  
## <a name="configuring-the-log-provider"></a>Настройка регистратора  
  
### <a name="initializing-the-log-provider"></a>Инициализация регистратора  
 Необходимо переопределить метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.InitializeLogProvider%2A> для кэширования ссылок на коллекцию соединений и интерфейс событий. В дальнейшем можно использовать эти кэшированные ссылки в других методах регистратора.  
  
### <a name="using-the-configstring-property"></a>Использование свойства ConfigString  
 Во время разработки регистратор получает данные конфигурации из столбца **Конфигурация**. Эти данные конфигурации соответствуют свойству <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> регистратора. По умолчанию этот столбец содержит текстовое поле, из которого можно получить любые строковые данные. Большинство регистраторов, включенных в службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], используют это свойство для хранения имени диспетчера соединений, которое регистратор применяет для соединения с внешним источником данных. Если выбранный регистратор использует свойство <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A>, используйте метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A>, чтобы проверить это свойство и убедиться, что оно имеет правильное значение.  
  
### <a name="validating-the-log-provider"></a>Проверка регистратора  
 Необходимо переопределить метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A>, чтобы убедиться в правильности настройки регистратора и его готовности к выполнению. Обычно, чтобы убедиться в правильности настройки <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A>, требуется минимальный уровень проверки. Выполнение не может продолжиться, пока регистратор не возвратит значение <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> из метода <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A>.  
  
 В следующем примере кода демонстрируется реализация метода <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A>, которая проверяет, что имя диспетчера соединений указано, что диспетчер соединений существует в пакете и что диспетчер соединений возвращает имя файла в свойстве <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A>.  
  
```csharp  
public override DTSExecResult Validate(IDTSInfoEvents infoEvents)  
{  
    if (this.ConfigString.Length == 0 || connections.Contains(ConfigString) == false)  
    {  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
        return DTSExecResult.Failure;  
    }  
    else  
    {  
        string fileName = connections[ConfigString].AcquireConnection(null) as string;  
  
        if (fileName == null || fileName.Length == 0)  
        {  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
            return DTSExecResult.Failure;  
        }  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As IDTSInfoEvents) As DTSExecResult  
    If Me.ConfigString.Length = 0 Or connections.Contains(ConfigString) = False Then  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
        Return DTSExecResult.Failure  
    Else   
        Dim fileName As String =  connections(ConfigString).AcquireConnectionCType(as string, Nothing)  
  
        If fileName = Nothing Or fileName.Length = 0 Then  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
            Return DTSExecResult.Failure  
        End If  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
### <a name="persisting-the-log-provider"></a>Сохраняемость регистратора  
 Как правило, нет необходимости реализовывать пользовательский механизм сохраняемости для диспетчера соединений. Нестандартный механизм сохраняемости необходим только в случае, когда свойства объекта используют сложные типы данных. Дополнительные сведения см. в разделе [Разработка пользовательских объектов для служб Integration Services](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md).  
  
## <a name="logging-with-the-log-provider"></a>Ведение журнала с помощью регистратора  
 Существуют три метода времени выполнения, которые должны быть переопределены всеми регистраторами: <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>  
  
> [!IMPORTANT]  
>  Во время проверки и выполнения одного пакета методы <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> вызываются более одного раза. Убедитесь, что пользовательский код не приведет к перезаписи более ранних записей журнала при следующем открытии и закрытии журнала. Если была выбрана регистрация событий проверки в тестовом пакете, первым зарегистрированным событием должно быть событие OnPreValidate. Если вместо него первым событием в журнале отображается PackageStart, начальные события проверки были перезаписаны.  
  
### <a name="opening-the-log"></a>Открытие журнала  
 Большинство регистраторов соединяются с внешним источником данных, например с файлом или базой данных, чтобы сохранять данные событий, которые собираются в ходе выполнения пакета. Как и в случае с любым другим объектом в среде выполнения, соединение с внешним источником данных обычно устанавливается с помощью объектов диспетчера соединений.  
  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> вызывается в начале выполнения пакета. Переопределите этот метод, чтобы установить соединение с внешним источником данных.  
  
 В следующем образце кода демонстрируется регистратор, который открывает текстовый файл для записи во время выполнения метода <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>. Файл открывается путем вызова метода <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> диспетчера соединений, который был указан в свойстве <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A>.  
  
```csharp  
public override void OpenLog()  
{  
    if(!this.connections.Contains(this.ConfigString))  
        throw new Exception("The ConnectionManager " + this.ConfigString + " does not exist in the Connections collection.");  
  
    this.connectionManager = connections[ConfigString];  
    string filePath = this.connectionManager.AcquireConnection(null) as string;  
  
    if(filePath == null || filePath.Length == 0)  
        throw new Exception("The ConnectionManager " + this.ConfigString + " is not a valid FILE ConnectionManager");  
  
    //  Create a StreamWriter to append to.  
    sw = new StreamWriter(filePath,true);  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString());  
}  
```  
  
```vb  
Public Overrides  Sub OpenLog()  
    If Not Me.connections.Contains(Me.ConfigString) Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " does not exist in the Connections collection.")  
    End If  
  
    Me.connectionManager = connections(ConfigString)  
    Dim filePath As String =  Me.connectionManager.AcquireConnectionCType(as string, Nothing)  
  
    If filePath = Nothing Or filePath.Length = 0 Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " is not a valid FILE ConnectionManager")  
    End If  
  
    '  Create a StreamWriter to append to.  
    sw = New StreamWriter(filePath,True)  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString())  
End Sub  
```  
  
### <a name="writing-log-entries"></a>Создание записей журнала  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> вызывается каждый раз, когда объект в пакете инициирует событие путем вызова метода Fire\<событие> для одного из интерфейсов события. Каждое событие инициируется со сведениями о его контексте и обычно дополняется поясняющим сообщением. Однако не каждый вызов метода <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> включает сведения о каждом параметре метода. Например, некоторые стандартные события, имена которых очевидны без пояснений, не предоставляют параметров MessageText, а параметры DataCode и DataBytes предназначены для необязательных вспомогательных сведений.  
  
 В следующем примере кода реализуется метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> и события записываются в поток, открытый в предыдущем разделе.  
  
```csharp  
public override void Log(string logEntryName, string computerName, string operatorName, string sourceName, string sourceID, string executionID, string messageText, DateTime startTime, DateTime endTime, int dataCode, byte[] dataBytes)  
{  
    sw.Write(logEntryName + ",");  
    sw.Write(computerName + ",");  
    sw.Write(operatorName + ",");  
    sw.Write(sourceName + ",");  
    sw.Write(sourceID + ",");  
    sw.Write(messageText + ",");  
    sw.Write(dataBytes + ",");  
    sw.WriteLine("");  
}  
```  
  
```vb  
Public Overrides  Sub Log(ByVal logEnTryName As String, ByVal computerName As String, ByVal operatorName As String, ByVal sourceName As String, ByVal sourceID As String, ByVal executionID As String, ByVal messageText As String, ByVal startTime As DateTime, ByVal endTime As DateTime, ByVal dataCode As Integer, ByVal dataBytes() As Byte)  
    sw.Write(logEnTryName + ",")  
    sw.Write(computerName + ",")  
    sw.Write(operatorName + ",")  
    sw.Write(sourceName + ",")  
    sw.Write(sourceID + ",")  
    sw.Write(messageText + ",")  
    sw.Write(dataBytes + ",")  
    sw.WriteLine("")  
End Sub  
```  
  
### <a name="closing-the-log"></a>Закрытие журнала  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> вызывается в конце выполнения пакета, после того как все объекты в пакете завершили выполнение (либо если выполнение пакета остановлено в связи с ошибками).  
  
 В следующем примере кода демонстрируется реализация метода <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>, которая закрывает файловый поток, открытый при выполнении метода <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>.  
  
```csharp  
public override void CloseLog()  
{  
    if (sw != null)  
    {  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString());  
        sw.Close();  
    }  
}  
```  
  
```vb  
Public Overrides  Sub CloseLog()  
    If Not sw Is Nothing Then  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString())  
        sw.Close()  
    End If  
End Sub  
```  
 
## <a name="see-also"></a>См. также:  
 [Создание пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/creating-a-custom-log-provider.md)   
 [Разработка пользовательского интерфейса для пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-user-interface-for-a-custom-log-provider.md)  
  
  

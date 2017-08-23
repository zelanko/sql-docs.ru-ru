---
title: "Подключение к источникам данных в компоненте скрипта | Документы Microsoft"
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
helpviewer_keywords:
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2accca553f1bd9c536076fd0bbcebbff0ff2c42
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-component"></a>Соединение с источниками данных в компоненте скрипта
  Диспетчер соединений — это удобный элемент, который инкапсулирует и сохраняет сведения, необходимые для соединения с источником данных определенного типа. Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](../../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 Выполненные существующих диспетчеров соединений доступ для пользовательского скрипта в компоненте источника или назначения, нажав кнопку **добавить** и **удалить** кнопок, расположенных на **диспетчеры соединений** страница **редактор преобразования «скрипт»**. Однако необходимо написать собственный пользовательский код для загрузки и сохранения данных, а также, возможно, для открытия и закрытия соединения с источником данных. Дополнительные сведения о **диспетчеры соединений** страница **редактор преобразования «скрипт»**, в разделе [Настройка компонента скрипта в редакторе компонентов скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md) и [редактор преобразования «скрипт» &#40; Страница «Диспетчеры соединений» &#41; ](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
 Компонент скрипта создает **подключений** класс коллекции в **ComponentWrapper** элемент проекта, который содержит строго типизированных методов доступа для каждого диспетчера соединений, который имеет имя, совпадающее с именем самого диспетчера соединений. Эта коллекция предоставляется через **подключений** свойство **ScriptMain** класса. Свойство метода доступа возвращает ссылку на диспетчер соединений как на экземпляр <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>. Например, если добавить диспетчер соединений с именем `MyADONETConnection` на странице «Диспетчеры соединений» диалогового окна, можно получить ссылку на него в скрипте, добавив следующий код:  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  Необходимо знать тип соединения, возвращаемого диспетчером соединений перед вызовом метода **AcquireConnection**. Поскольку в задаче «скрипт» **Option Strict** включен, необходимо привести соединение, которое возвращается в виде типа **объекта**, к подходящему типу соединения перед его использованием.  
  
 После этого нужно вызвать **AcquireConnection** метод в диспетчер подключения, чтобы получить Базовое соединение или сведения, необходимые для подключения к источнику данных. Например, можно получить ссылку на **System.Data.SqlConnection** оболочкой диспетчер соединений ADO.NET с помощью следующего кода:  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 Вместе с тем тот же вызов к диспетчеру соединений с неструктурированными файлами вернет только путь и имя файла источника данных.  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 Затем необходимо предоставить этот путь и имя файла для **System.IO.StreamReader** или **Streamwriter** для чтения или записи данных в неструктурированном файле.  
  
> [!IMPORTANT]  
>  При написании управляемого кода в компоненте скрипта, невозможно вызвать метод AcquireConnection соединения диспетчеров, которые возвращают неуправляемые объекты, такие как диспетчер соединений OLE DB и диспетчер соединений Excel. Тем не менее, можно считать свойство ConnectionString этих диспетчеров соединений и подключиться к источнику данных непосредственно в коде с помощью строки подключения объекта OLEDB **подключения** из **System.Data.OleDb** пространства имен.  
>   
>  Если необходимо вызвать метод AcquireConnection диспетчера соединений, возвращающего неуправляемый объект, используют диспетчер соединений ADO.NET. При настройке диспетчера соединений ADO.NET для использования поставщика OLE DB он соединяется с помощью поставщика данных .NET Framework для OLE DB. В этом случае метод AcquireConnection возвращает **System.Data.OleDb.OleDbConnection** вместо неуправляемого объекта. Чтобы настроить диспетчер соединений ADO.NET для использования с источником данных Excel, выберите поставщик Microsoft OLE DB для Jet, укажите книгу Excel, а затем введите `Excel 8.0` (для Excel 97 и более поздних версий) в качестве значения **расширенные свойства** на **все** страница **диспетчера соединений** диалоговое окно.  
  
 Дополнительные сведения об использовании диспетчеров соединений в компоненте скрипта см. в разделе [Создание источника с помощью компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) и [Создание назначения с помощью компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services &#40; Службы SSIS &#41; Подключения](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Создание диспетчеров соединений](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  

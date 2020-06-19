---
title: Подключение к источникам данных в компоненте скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 0fb6ccc97c2f0f5a3a69d2caa61ca67327015415
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967284"
---
# <a name="connecting-to-data-sources-in-the-script-component"></a>Соединение с источниками данных в компоненте скрипта
  Диспетчер соединений — это удобный элемент, который инкапсулирует и сохраняет сведения, необходимые для соединения с источником данных определенного типа. Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](../../connection-manager/integration-services-ssis-connections.md).  
  
 Можно сделать существующие диспетчеры подключений доступными для пользовательского скрипта в компоненте источника или назначения, нажимая кнопки **Добавить** и **Удалить** на странице **Диспетчеры подключений** в окне **Редактор преобразования "Скрипт"** . Однако необходимо написать собственный пользовательский код для загрузки и сохранения данных, а также, возможно, для открытия и закрытия соединения с источником данных. Дополнительные сведения о странице **Диспетчеры подключений** окна **Редактор преобразования "скрипт"** см. в разделах [Настройка компонента скрипта в редакторе компонента скрипта](configuring-the-script-component-in-the-script-component-editor.md) и [Редактор преобразования "Скрипт" (страница "Диспетчеры подключений")](../../script-transformation-editor-connection-managers-page.md).  
  
 Компонент скрипта создает класс коллекции `Connections` в элементе проекта `ComponentWrapper`, который содержит строго типизированный метод доступа для каждого диспетчера соединений, имя которого совпадает с именем самого диспетчера соединений. Эта коллекция доступна с помощью свойства `Connections` класса `ScriptMain`. Свойство метода доступа возвращает ссылку на диспетчер соединений как на экземпляр <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>. Например, если добавить диспетчер соединений с именем `MyADONETConnection` на странице «Диспетчеры соединений» диалогового окна, можно получить ссылку на него в скрипте, добавив следующий код:  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  Прежде чем вызывать метод `AcquireConnection`, необходимо узнать тип соединения, возвращаемого диспетчером соединений. Поскольку в задаче «Скрипт» включен параметр `Option Strict`, перед использованием необходимо привести соединение, возвращаемое с типом `Object`, к подходящему типу соединения.  
  
 Далее, необходимо вызвать метод `AcquireConnection` конкретного диспетчера соединений, чтобы получить базовое соединение либо сведения, необходимые для соединения с источником данных. Например, с помощью следующего кода можно получить ссылку на подключение **System.Data.SqlConnection**, упакованное диспетчером подключений ADO.NET:  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 Вместе с тем тот же вызов к диспетчеру соединений с неструктурированными файлами вернет только путь и имя файла источника данных.  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 Затем необходимо предоставить этот путь и имя файла модулю чтения `System.IO.StreamReader`, или модулю записи `Streamwriter` для чтения, или записи данных в неструктурированный файл.  
  
> [!IMPORTANT]  
>  При написании управляемого кода в компоненте скрипта нельзя вызывать метод AcquireConnection диспетчеров подключений, возвращающий неуправляемые объекты, например диспетчера подключений OLE DB или диспетчера подключений Excel. Однако можно считать свойство ConnectionString этих диспетчеров подключений и подключиться к источнику данных непосредственно в коде с помощью строки подключения объекта OLEDB **connection** из пространства имен **System.Data.OleDb**.  
>   
>  Если необходимо вызвать метод AcquireConnection диспетчера подключений, возвращающего неуправляемый объект, используйте диспетчер подключений ADO.NET. При настройке диспетчера соединений ADO.NET для использования поставщика OLE DB он соединяется с помощью поставщика данных .NET Framework для OLE DB. В этом случае метод AcquireConnection возвращает `System.Data.OleDb.OleDbConnection` вместо неуправляемого объекта. Чтобы настроить диспетчер подключений ADO.NET для работы с источником данных Excel, выберите "Поставщик OLE DB для Jet (Майкрософт)", укажите книгу Excel, а затем введите `Excel 8.0` (для Excel 97 и более поздних версий) в качестве значения параметра **Расширенные свойства** на странице **Все** диалогового окна **Диспетчер подключений**.  
  
 Дополнительные сведения об использовании диспетчеров подключений в компоненте скрипта см. в разделах [Создание источника с помощью компонента скрипта](../../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) и [Создание назначения с помощью компонента скрипта](../../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;соединений&#41; SSIS](../../connection-manager/integration-services-ssis-connections.md)   
 [Создание диспетчеров соединений](../../create-connection-managers.md)  
  
  

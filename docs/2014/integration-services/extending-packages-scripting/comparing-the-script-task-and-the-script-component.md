---
title: Сравнение задачи "Скрипт" и компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], comparing to Script component
- Script component [Integration Services], comparing to Script task
ms.assetid: 4b73753a-4239-491b-b7a6-abc63ba83d2d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c08545341e3ecfe8c82ab01723d96167412e1b03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62895023"
---
# <a name="comparing-the-script-task-and-the-script-component"></a>Сравнение задачи «Скрипт» и компонента скрипта
  Задача "Скрипт", доступная в окне "Поток управления" конструктора служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], и компонент скрипта, доступный в окне "Поток данных", предназначены в пакете служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для разных целей. Задача представляет собой универсальное средство потока управления, а компонент служит источником, преобразованием или назначением в потоке данных. Несмотря на то что они предназначены для разных целей, между задачей «Скрипт» и компонентом скрипта имеются некоторые подобия в используемых средствах разработки кода и объектах в пакете, которые доступны разработчику с их помощью. Понимание их подобия и различия может помочь использовать задачи и компоненты более эффективно.  
  
## <a name="similarities-between-the-script-task-and-the-script-component"></a>Подобия между задачей «Скрипт» и компонентом скрипта  
 Задача «Скрипт» и компонент скрипта имеют следующие общие характеристики.  
  
|Компонент|Description|  
|-------------|-----------------|  
|Два режима времени разработки|Разработка задачи и компонента начинается с определения свойств в редакторе с последующим переключением в среду разработки для написания кода.|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Средства для приложений (VSTA)|И для задачи и для компонента используется одна и та же интегрированная среда разработки средств VSTA, а поддерживающий код пишется на языке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic либо [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.|  
|Предварительно откомпилированные скрипты|Начиная с версии служб [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], все скрипты предварительно компилируются. В более ранних версиях предусмотрена возможность указать, должны ли скрипты быть предварительно откомпилированы.<br /><br /> Предварительная компиляция скрипта приводит к получению двоичного кода, который позволяет повысить быстродействие выполнения, но за счет увеличенного размера пакета.|  
|Отладка|И в задаче и в компоненте поддерживаются точки останова и пошаговое выполнение кода во время отладки в среде разработки. Дополнительные сведения см. в статьях [кодирование и отладка задачи «Скрипт](../control-flow/script-task.md) » и [программирование и отладка компонента скрипта] (.. /екстендинг-паккажес-скриптинг/дата-флов-скрипт-компонент/кодинг-анд-дебуггинг-се-скрипт-компонент.мд.|  
  
## <a name="differences-between-the-script-task-and-the-script-component"></a>Различия между задачей «Скрипт» и компонентом скрипта  
 Между задачей «Скрипт» и компонентом скрипта имеются следующие различия.  
  
|Компонент|Задача «Скрипт»|Компонент скрипта|  
|-------------|-----------------|----------------------|  
|Поток управления или поток данных|Настройка задачи «Скрипт» выполняется на вкладке «Поток управления» конструктора и запускается вне потока данных пакета.|Настройка компонента скрипта выполняется на странице конструктора «Поток данных», а компонент представляет источник, преобразование или назначение в задаче потока данных.|  
|Назначение|Задача «Скрипт» позволяет выполнять почти любую задачу общего назначения.|С помощью компонента скрипта можно указать, следует ли создать источник, преобразование или назначение.|  
|Выполнение|Задача «Скрипт» запускает пользовательский код в определенной точке рабочего процесса пакета. Если задача не помещена в контейнер цикла или обработчик события, она выполняется только один раз.|Компонент скрипта также выполняется однократно, но, как правило, он выполняет свою главную процедуру обработки по одному разу для каждой строки данных в потоке данных.|  
|Редактор|
  **Редактор задачи "Скрипт"** содержит три страницы: **Общие**, **Скрипт** и **Выражения**. Только свойства, и ScriptLanguage непосредственно влияют на код, который можно написать. **** `ReadOnlyVariables` `ReadWriteVariables`|
  **Редактор преобразования "Скрипт"** может содержать до четырех страниц: **Входные столбцы**, **Входы и выходы**, **Скрипт** и **Диспетчер подключений**. Каждая из этих страниц предназначена для настройки метаданных и свойств, определяющих, какие элементы базовых классов автоматически формируются для использования при разработке кода.|  
|Взаимодействие с пакетом|В коде, написанном для задачи «Скрипт», для доступа к другим функциям пакета используется свойство `Dts`. Свойство `Dts` является элементом класса `ScriptMain`.|В коде компонента скрипта используются свойства типизированного метода доступа для получения доступа к определенным средствам пакета, таким как переменные и диспетчеры соединений.<br /><br /> Метод `PreExecute` может обращаться только к переменным, доступным только для чтения. Метод `PostExecute` может обращаться как к переменным, доступным только для чтения, так и к переменным, доступным для чтения и записи.<br /><br /> Дополнительные сведения об этих методах см. в разделе [программирование и отладка компонента скрипта] (. /екстендинг-паккажес-скриптинг/дата-флов-скрипт-компонент/кодинг-анд-дебуггинг-се-скрипт-компонент.мд.|  
|Использование переменных|Задача «Скрипт» использует <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> свойство `Dts` объекта для доступа к переменным, доступным в свойствах задачи <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> и. <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> Пример:<br /><br /> **VB**<br /><br /> `Dim myVar as String myVar = Dts.Variables("MyStringVariable").Value.ToString`<br /><br /> <br /><br /> **См**<br /><br /> `string myVar; myVar = Dts.Variables["MyStringVariable"].Value.ToString();`|В компоненте скрипта используются свойства типизированного метода доступа, относящиеся к автоматически сформированному базовому классу, который создан на основе свойств компонентов <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A>. Пример:<br /><br /> **VB**<br /><br /> `Dim myVar as String myVar = Me.Variables.MyStringVariable`<br /><br /> <br /><br /> **См**<br /><br /> `string myVar; myVar = this.Variables.MyStringVariable;`|  
|Использование соединений|Чтобы получить доступ к диспетчерам соединений, определенным в пакете, в задаче «Скрипт» используется свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> объекта `Dts`. Пример:<br /><br /> **VB**<br /><br /> `Dim myFlatFileConnection As String myFlatFileConnection = _     DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _     String)`<br /><br /> <br /><br /> **См**<br /><br /> `string myFlatFileConnection; myFlatFileConnection = (Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);`|В компоненте скрипта используются свойства типизированного метода доступа, относящиеся к автоматически сформированному базовому классу, который создан на основе списка диспетчеров соединений, введенного пользователем на странице «Диспетчеры соединений» редактора. Пример:<br /><br /> **VB**<br /><br /> `Dim connMgr As IDTSConnectionManager100 connMgr = Me.Connections.MyADONETConnection`<br /><br /> <br /><br /> **См**<br /><br /> `IDTSConnectionManager100 connMgr; connMgr = this.Connections.MyADONETConnection;`|  
|Инициирование событий|В задаче «Скрипт» для инициирования событий используется свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> объекта `Dts`. Пример:<br /><br /> **VB**<br /><br /> `Dts.Events.FireError(0, "Event Snippet", _     ex.Message & ControlChars.CrLf & ex.StackTrace, _     "", 0)`<br /><br /> <br /><br /> **См**<br /><br /> `Dts.Events.FireError(0, "Event Snippet", ex.Message + "\r" + ex.StackTrace, "", 0);`|Компонент скрипта инициирует ошибки, предупреждения и информационные сообщения с помощью методов интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, возвращаемых свойством <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>. Пример:<br /><br /> **VB**<br /><br /> `Dim myMetadata as IDTSComponentMetaData100 myMetaData = Me.ComponentMetaData myMetaData.FireError(...)`|  
|Logging|Задача «Скрипт» использует <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> метод `Dts` объекта для записи сведений о включенных регистраторах. Пример:<br /><br /> **VB**<br /><br /> `Dim bt(0) As Byte Dts.Log("Test Log Event", _     0, _     bt)`<br /><br /> <br /><br /> **См**<br /><br /> `byte[] bt = new byte[0]; Dts.Log("Test Log Event", 0, bt);`|В компоненте скрипта используется метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> автоформирования базового класса для ведения журналов во включенных регистраторах. Пример:<br /><br /> **VB**<br /><br /> `Dim bt(0) As Byte`<br /><br /> `Me.Log("Test Log Event", _`<br /><br /> `0, _`<br /><br /> `bt)`<br /><br /> <br /><br /> **См**<br /><br /> `byte[] bt = new byte[0]; this.Log("Test Log Event", 0, bt);`|  
|Возвращение результатов|Задача «Скрипт» использует как <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> свойство, так и <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> необязательное `Dts` свойство объекта для уведомления среды выполнения о ее результатах.|Компонент скрипта выполняется в составе задачи потока данных и не сообщает о результатах ни с одним из этих свойств.|  
  
## <a name="see-also"></a>См. также:  
 [Расширение пакета с помощью задачи «Скрипт»](task/extending-the-package-with-the-script-task.md)   
 [Расширение потока данных с помощью компонента скрипта](data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
 [Использование задачи «Скрипт» в SQL Server Integration Services SSIS для подключения к веб-службе](https://www.mssqltips.com/sqlservertip/4288/using-a-script-task-in-sql-server-integration-services-ssis-to-connect-to-a-web-service/)  
  
  

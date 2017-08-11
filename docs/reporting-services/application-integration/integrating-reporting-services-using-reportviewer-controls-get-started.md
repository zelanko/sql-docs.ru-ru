---
title: "Приступая к работе с элементом управления ReportViewer 2016 | Документы Microsoft"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 6e1d0305fff039aad4d387cbc63026f40db9f97e
ms.openlocfilehash: 9d229fd4764da21612d1b1cf532f1beaf8116769
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls---get-started"></a>Интеграция службы Reporting Services с помощью элементов управления ReportViewer — начало работы

Узнайте, как разработчики могут встроить разбиением на страницы в веб-сайтов ASP.Net и приложений Windows forms, через службы Reporting Services 2016 элемента управления ReportViewer. Можно добавить элемент управления в новый проект или обновите существующий проект.

## <a name="adding-the-reportviewer-control-to-a-new-web-project"></a>Добавление элемента управления ReportViewer для нового веб-проекта

1. Создайте новый **пустой веб-сайт ASP.NET** или откройте существующий проект ASP.NET.

    ![службы ssRS — Создание-нового-ASPNET-проекта](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. Установка пакета nuget элемента управления ReportViewer 2016 через **консоли диспетчера пакетов Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. Добавьте в проект новый ASPX-страницы и зарегистрировать сборку элемента управления ReportViewer для использования на странице.

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. Добавить **ScriptManagerControl** на страницу.

5. Добавьте элемент управления ReportViewer на страницу. В приведенном ниже фрагменте можно обновить для ссылки на отчет, размещенной на удаленном сервере отчетов.

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
Окончательный страница должна выглядеть следующим образом.

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Sample" %>

<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <meta http-equiv="X-UA-Compatible" content="IE=edge" /> 
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
    <asp:ScriptManager runat="server"></asp:ScriptManager>        
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
            <ServerReport ReportServerUrl="http://AContosoDepartment/ReportServer" ReportPath="/LatestSales" />
        </rsweb:ReportViewer>
    </form>
</body>
</html>

```

## <a name="updating-an-existing-project-to-use-the-reportviewer-control"></a>Обновление существующего проекта, чтобы использовать элемент управления ReportViewer

Чтобы использовать элемент управления ReportViewer 2016 в существующий проект, добавить элемент управления с помощью Nuget и обновить ссылки на сборки до версии *14.0.0.0*. Сюда входят обновления проекта web.config и все ASPX-страницы, которые ссылаются на элемент управления ReportViewer.

### <a name="sample-webconfig-changes"></a>Пример web.config изменения

```
<?xml version="1.0"?>
<!--
  For more information on how to configure your ASP.NET application, please visit
  http://go.microsoft.com/fwlink/?LinkId=169433
  -->
<configuration>
  <system.web>
    <compilation debug="true" targetFramework="4.5.2">
      <assemblies>
        <!-- All assemblies updated to version 14.0.0.0. -->
        <add assembly="Microsoft.ReportViewer.Common, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.DataVisualization, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.Design, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.ProcessingObjectModel, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebDesign, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WinForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </assemblies>
      <buildProviders>
        <!-- Version updated to 14.0.0.0. -->
        <add extension=".rdlc"
          type="Microsoft.Reporting.RdlBuildProvider, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </buildProviders>
    </compilation>
    <httpRuntime targetFramework="4.5.2"/>
    <httpHandlers>
      <!-- Version updated to 14.0.0.0 -->
      <add path="Reserved.ReportViewerWebControl.axd" verb="*"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"
        validate="false"/>
    </httpHandlers>
  </system.web>
  <system.webServer>
    <validation validateIntegratedModeConfiguration="false"/>
    <modules runAllManagedModulesForAllRequests="true"/>
    <handlers>
      <!-- Version updated to 14.0.0.0 -->
      <add name="ReportViewerWebControlHandler" verb="*" path="Reserved.ReportViewerWebControl.axd" preCondition="integratedMode"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
    </handlers>
  </system.webServer>
</configuration>
```

### <a name="sample-aspx"></a>Образец .aspx

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 14.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-reportviewer-control-to-a-new-windows-forms-project"></a>Добавление элемента управления ReportViewer в новый проект Windows forms

1. Создайте новый **приложение Windows Forms** или откройте существующий проект.

    ![службы ssRS — Создание-нового winforms проекта](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. Установка пакета nuget элемента управления ReportViewer 2016 через **консоли диспетчера пакетов Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. Добавить новый элемент управления из кода или [добавьте элемент управления в область элементов](##adding-control-to-visual-studio-toolbar).

    ```
    private Microsoft.Reporting.WinForms.ReportViewer reportViewer1;
    
    private void InitializeComponent()
    {
        this.reportViewer1 = new Microsoft.Reporting.WinForms.ReportViewer();
        this.SuspendLayout();
        // 
        // reportViewer1
        // 
        this.reportViewer1.Location = new System.Drawing.Point(168, 132);
        this.reportViewer1.Name = "reportViewer1";
        this.reportViewer1.ServerReport.BearerToken = null;
        this.reportViewer1.Size = new System.Drawing.Size(396, 246);
        this.reportViewer1.TabIndex = 0;
        // 
        // Form1
        // 
        this.Controls.Add(this.reportViewer1);
    }
    ```

## <a name="how-to-set-100-height-on-the-report-viewer-2016-control"></a>Как задать высоту 100% для управления 2016 средства просмотра отчетов

Новый элемент управления 2016 средства просмотра отчетов оптимизирован для ориентации страниц стандарты HTML5 и работает на всех современных браузеров. В прошлом, с помощью старого RVC элемента управления при установке свойства высоты 100%, он работал даже если ни один из родительских высоте, указанной. Это поведение изменено в HTML5. При установке этого свойства для нового элемента управления RVC, он будет работать только в том случае, если родительский элемент имеет определенный высоту, т. е. не значение auto или всех предков RVC иметь высоты 100% слишком.

Ниже приведены два примера это сделать.

### <a name="by-setting-the-height-of-all-the-parent-elements-to-100"></a>Установив высоту всех родительских элементов до 100%

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <style>
        html,body,form,#div1 {
            height: 100%; 
        }
    </style>
   </head>
<body>
    <form id="form1" runat="server">
    <div id="div1" >
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

### <a name="by-setting-the-style-height-attribute-on-the-parent-of-the-reportviewer-control"></a>Установив высоту атрибута стиля для родительского элемента управления reportviewer

Дополнительные сведения о процент длины окна просмотра. в разделе [просмотра процент длины](https://www.w3.org/TR/css3-values/#viewport-relative-lengths).

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
</head>
<body>
    <form id="form1" runat="server">
    <div style="height:100vh;">
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

## <a name="adding-control-to-visual-studio-toolbar"></a>Добавление элемента управления панели инструментов Visual Studio

Элемент управления средства просмотра отчетов теперь поставляется в виде пакета NuGet. По этой причине не будет отображаться в панели элементов Visual Studio по умолчанию элемент управления средства просмотра отчетов. Элемент управления можно добавить на панель элементов следующим образом.

1. Установка пакета NuGet для WinForms или WebForms, как было сказано выше.

2. Удалите элемент управления ReportViewer, который указан в области элементов. Это элемент управления с помощью версии 12.x.

    ![службы ssRS-remove старого rvcontrol элементов](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. Щелкните правой кнопкой мыши в любом месте на панели инструментов, а затем выберите **Выбор элементов...** .

    ![службы ssRS элемент панели инструментов выберите](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. На **компоненты .NET Framework**выберите **Обзор**.

    ![службы ssRS, панель элементов, Обзор](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. Выберите **Microsoft.ReportViewer.WinForms.dll** или **Microsoft.ReportViewer.WebForms.dll** из установки пакета NuGet.

    > [!NOTE] 
    > В каталоге решения проекта будет установлен пакет NuGet. Путь к библиотеке dll будет подобен следующему: `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` или `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`.

6. Новый элемент управления должно отображаться в панели элементов. Можно переместить ее на другую вкладку в панели элементов при необходимости.

    ![службы ssRS, панель элементов, rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

### <a name="things-to-be-aware-of"></a>Необходимо иметь в виду следующее

- Это будет добавьте ссылку в установленном пакете NuGet текущего проекта. Элемент на панели элементов, сохранятся в другие проекты. При установке пакета NuGet в новое решение или проект, элемент панели инструментов могут ссылаться на более старую версию. 

- Элемент управления остается в области элементов, даже если сборка доступна не больше. Если этот проект был удален, если вы повторите и добавьте элемент управления из области элементов Visual Studio вызовет ошибку. Чтобы исправить эту ошибку, удалите элемент управления из панели элементов и повторно добавить его, используя описанные выше шаги.


## <a name="common-issues"></a>Распространенные проблемы
    
- Элемент управления ReportViewer 2016 предназначен для использования с современными браузерами. Элемент управления может работать, если браузер отображает веб-страницы в режиме совместимости с IE. Узлы интрасети может потребоваться метатег для переопределения параметра которой стимулировать Подготовка к просмотру страниц интрасети в режиме совместимости.

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="providing-feedback"></a>Обратная связь

Разрешить команды знать о проблемах, которые встречаются с элементом управления [форумы Reporting Services MSDN](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices) или по электронной почте [ RVCFeedback@microsoft.com ](mailto:RVCFeedback@microsoft.com).

## <a name="see-also"></a>См. также:

[Сбор данных в элементе управления ReportingViewer 2016](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
Дополнительные вопросы? [Повторите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)



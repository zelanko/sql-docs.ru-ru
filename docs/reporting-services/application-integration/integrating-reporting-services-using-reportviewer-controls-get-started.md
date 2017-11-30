---
title: "Приступая к работе с элементом управления ReportViewer 2016 | Документы Майкрософт"
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
caps.latest.revision: "12"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Active
ms.openlocfilehash: dff598efce33f778359c2b6fb4c3a0184f2b88f6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="integrating-reporting-services-using-reportviewer-controls---get-started"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer — начало работы

Узнайте, как разработчики могут внедрять отчеты с разбиением на страницы на веб-сайты ASP.NET и в приложения Windows Forms с помощью элемента управления ReportViewer служб Reporting Services 2016. Можно добавить элемент управления в новый проект или обновить существующий проект.

## <a name="adding-the-reportviewer-control-to-a-new-web-project"></a>Добавление элемента управления ReportViewer в новый веб-проект

1. Создайте новый **пустой веб-сайт ASP.NET** или откройте существующий проект ASP.NET.

    ![ssRS-Create-New-ASPNET-Project](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. Установите пакет NuGet элемента управления ReportViewer 2016 с помощью **консоли диспетчера пакетов Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. Добавьте в проект новую ASPX-страницу и зарегистрируйте сборку элемента управления ReportViewer для использования на странице.

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. Добавьте на страницу **ScriptManagerControl**.

5. Добавьте на страницу элемент управления ReportViewer. Приведенный ниже фрагмент кода можно изменить для ссылки на отчет, размещенный на удаленном сервере отчетов.

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
Итоговая страница должна иметь следующий вид:

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

## <a name="updating-an-existing-project-to-use-the-reportviewer-control"></a>Обновление существующего проекта для использования элемента управления ReportViewer

Чтобы использовать элемент управления ReportViewer 2016 в существующем проекте, добавьте элемент управления с помощью пакета NuGet и обновите ссылки на сборку до версии *14.0.0.0*. Необходимо обновить файл web.config проекта и все ASPX-страницы проекта, которые ссылаются на элемент управления ReportViewer.

### <a name="sample-webconfig-changes"></a>Пример изменений web.config

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

### <a name="sample-aspx"></a>Пример ASPX

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 14.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-reportviewer-control-to-a-new-windows-forms-project"></a>Добавление элемента управления ReportViewer в новый веб-проект Windows Forms

1. Создайте новое **приложение Windows Forms** или откройте существующий проект.

    ![ssRS-Create-New-winforms-Project](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. Установите пакет NuGet элемента управления ReportViewer 2016 с помощью **консоли диспетчера пакетов Nuget**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. Добавьте новый элемент управления из кода или [добавьте элемент управления на панель элементов](##adding-control-to-visual-studio-toolbar).

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

## <a name="how-to-set-100-height-on-the-report-viewer-2016-control"></a>Как задать высоту 100 % для элемента управления средства просмотра отчетов 2016

Новый элемент управления средства просмотра отчетов 2016 оптимизирован для страниц в стандартном режиме HTML5 и работает во всех современных браузерах. Ранее при установке свойства высоты в 100 % старый элемент управления RVC работал, даже если значение высоты не было задано ни для одного родительского элемента. В HTML5 это поведение изменилось. Если это свойство задать новому элементу управления RVC, элемент управления будет работать только в том случае, если родительский элемент имеет определенную высоту, т. е. не автоматически заданную, или высота всех предков RVC тоже составляет 100 %.

Ниже приведены два примера того, как это сделать.

### <a name="by-setting-the-height-of-all-the-parent-elements-to-100"></a>Путем установки высоты всех родительских элементов в 100 %

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

### <a name="by-setting-the-style-height-attribute-on-the-parent-of-the-reportviewer-control"></a>Путем установки высоты атрибута стиля для родительского элемента элемента управления reportviewer

Дополнительные сведения о размерах окна просмотра в процентах см. в разделе [Viewport-percentage lengths](https://www.w3.org/TR/css3-values/#viewport-relative-lengths) (Размеры окна просмотра в процентах).

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

## <a name="adding-control-to-visual-studio-toolbar"></a>Добавление элемента управления на панель элементов Visual Studio

Сейчас элемент управления средства просмотра отчетов поставляется в виде пакета NuGet. Поэтому он не будет отображаться на панели элементов Visual Studio по умолчанию. Чтобы добавить элемент управления на панель инструментов, выполните следующие действия.

1. Установите пакет NuGet для WinForms или WebForms, как было упомянуто выше.

2. Удалите элемент управления ReportViewer, указанный на панели элементов. Это элемент управления с версией 12.x.

    ![ssRS-remove-old-rvcontrol-toolbox](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. Щелкните правой кнопкой мыши где-либо на панели элементов и выберите пункт **Выбрать элементы..**.

    ![ssRS-toolbox-choose-item](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. В окне **Компоненты .NET Framework** щелкните **Обзор**.

    ![ssRS-toolbox-browse](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. В установленном пакете NuGet выберите **Microsoft.ReportViewer.WinForms.dll** или **Microsoft.ReportViewer.WebForms.dll**.

    > [!NOTE] 
    > Пакет NuGet будет установлен в каталоге решения. Путь к DLL будет иметь следующий вид: `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` или `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`.

6. Новый элемент управления должен появиться на панели элементов. При необходимости его можно переместить на другую вкладку в панели элементов.

    ![ssRS-toolbox-rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

### <a name="things-to-be-aware-of"></a>Необходимо учитывать следующие моменты:

- Будет добавлена ссылка на установленный пакете NuGet в текущем проекте. Элемент на панели элементов будет сохранен в другие проекты. При установке пакета NuGet в новое решение или проект элемент может ссылаться на более старую версию. 

- Элемент управления останется на панели элементов, даже если сборка больше не доступна. Если этот проект был удален, при попытке добавить элемент из панели элементов Visual Studio создаст исключение. Чтобы исправить эту ошибку, удалите элемент управления из панели элементов и повторно добавьте его, используя описанные выше шаги.


## <a name="common-issues"></a>Распространенные проблемы
    
- Элемент управления ReportViewer 2016 предназначен для использования в современных браузерах. Элемент управления может не работать, если браузер отображает веб-страницы в режиме совместимости с IE. Для сайтов интрасети может потребоваться метатег для переопределения параметра, что приведет к отображению страниц интрасети в режиме совместимости.

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="providing-feedback"></a>Отправка отзывов

Сообщите команде о проблемах, возникающих при работе с элементом управления, на [форумах MSDN по службам Reporting Services](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices) или по электронной почте [RVCFeedback@microsoft.com](mailto:RVCFeedback@microsoft.com).

## <a name="see-also"></a>См. также:

[Сбор данных в элементе управления ReportViewer 2016](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)


---
title: Приступая к работе с элементом управления ReportViewer 2016 | Документы Майкрософт
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: application-integration
ms.topic: conceptual
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 778ac08636656ad9b4598c0ac022fcc0a5e2284f
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50029473"
---
# <a name="integrating-reporting-services-using-the-report-viewer-controls---get-started"></a>Начало работы с интеграцией служб Reporting Services с помощью элементов управления средства просмотра отчетов

Элементы управления средства просмотра отчетов можно использовать для интеграции отчетов RDL Reporting Services в приложения WebForms и WinForms. Дополнительные сведения о последних обновлениях см. в статье с [описанием изменений](changelog.md).

## <a name="adding-the-report-viewer-control-to-a-new-web-project"></a>Добавление элемента управления средства просмотра отчетов в новый веб-проект

1. Создайте новый **пустой веб-сайт ASP.NET** или откройте существующий проект ASP.NET.

    ![ssRS-Create-New-ASPNET-Project](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. Установите пакет NuGet элемента управления средства просмотра отчетов с помощью **консоли диспетчера пакетов NuGet**.

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. Добавьте в проект новую ASPX-страницу и зарегистрируйте сборку элемента управления средства просмотра отчетов для использования на странице.

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. Добавьте на страницу **ScriptManagerControl**.

5. Добавьте на страницу элемент управления средства просмотра отчетов. Приведенный ниже фрагмент кода можно изменить для ссылки на отчет, размещенный на удаленном сервере отчетов.

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
Итоговая страница должна иметь следующий вид:

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Sample" %>

<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

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

## <a name="updating-an-existing-project-to-use-the-report-viewer-control"></a>Обновление имеющегося проекта для использования элемента управления средства просмотра отчетов

Обязательно обновите все ссылки на сборки до версии *15.0.0.0*, в том числе файл web.config проекта и все ASPX-страницы со ссылками на элемент управления "Средство просмотра".

### <a name="sample-webconfig-changes"></a>Пример изменений web.config

```
<?xml version="1.0"?>
<!--
  For more information on how to configure your ASP.NET application, please visit
  https://go.microsoft.com/fwlink/?LinkId=169433
  -->
<configuration>
  <system.web>
    <compilation debug="true" targetFramework="4.5.2">
      <assemblies>
        <!-- All assemblies updated to version 15.0.0.0. -->
        <add assembly="Microsoft.ReportViewer.Common, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.DataVisualization, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.Design, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.ProcessingObjectModel, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebDesign, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WinForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </assemblies>
      <buildProviders>
        <!-- Version updated to 15.0.0.0. -->
        <add extension=".rdlc"
          type="Microsoft.Reporting.RdlBuildProvider, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </buildProviders>
    </compilation>
    <httpRuntime targetFramework="4.5.2"/>
    <httpHandlers>
      <!-- Version updated to 15.0.0.0 -->
      <add path="Reserved.ReportViewerWebControl.axd" verb="*"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"
        validate="false"/>
    </httpHandlers>
  </system.web>
  <system.webServer>
    <validation validateIntegratedModeConfiguration="false"/>
    <modules runAllManagedModulesForAllRequests="true"/>
    <handlers>
      <!-- Version updated to 15.0.0.0 -->
      <add name="ReportViewerWebControlHandler" verb="*" path="Reserved.ReportViewerWebControl.axd" preCondition="integratedMode"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
    </handlers>
  </system.webServer>
</configuration>
```

### <a name="sample-aspx"></a>Пример ASPX

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 15.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-report-viewer-control-to-a-new-windows-forms-project"></a>Добавление элемента управления средства просмотра отчетов в новый веб-проект Windows Forms

1. Создайте новое **приложение Windows Forms** или откройте существующий проект.

    ![ssRS-Create-New-winforms-Project](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. Установите пакет NuGet элемента управления средства просмотра отчетов с помощью **консоли диспетчера пакетов NuGet**.

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

## <a name="how-to-set-100-height-on-the-report-viewer-control"></a>Способы настройки 100 % высоты для элемента управления средства просмотра отчетов

При задании значения 100 % для высоты элемента управления "Средство просмотра" необходимо установить для родительского элемента определенную высоту или настроить для всех предков процентное значение высоты.

### <a name="setting-the-height-of-all-the-ancestors-to-100"></a>Настройка значения высоты в 100 % для всех предков

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

### <a name="setting-the-parents-height-attribute"></a>Настройка атрибута высоты родительского элемента

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

Элемент управления средства просмотра отчетов теперь поставляется в виде пакета NuGet и больше не отображается на панели элементов Visual Studio по умолчанию. Вы можете добавить этот элемент управления на панель элементов вручную.

1. Установите пакет NuGet для WinForms или WebForms, как было упомянуто выше.

2. Удалите элемент управления средства просмотра отчетов, указанный на панели элементов.

    ![ssRS-remove-old-rvcontrol-toolbox](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. Щелкните правой кнопкой мыши где-либо на панели элементов и выберите пункт **Выбрать элементы...**

    ![ssRS-toolbox-choose-item](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. В окне **Компоненты .NET Framework** щелкните **Обзор**.

    ![ssRS-toolbox-browse](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. В установленном пакете NuGet выберите **Microsoft.ReportViewer.WinForms.dll** или **Microsoft.ReportViewer.WebForms.dll**.

    > [!NOTE] 
    > Пакет NuGet будет установлен в каталоге решения. Путь к DLL будет иметь следующий вид: `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` или `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`.

6. Новый элемент управления должен появиться на панели элементов. При необходимости его можно переместить на другую вкладку в панели элементов.

    ![ssRS-toolbox-rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

## <a name="common-issues"></a>Распространенные проблемы
    
Элемент управления "Средство просмотра" предназначено для современных браузеров. Этот элемент управления может работать некорректно, если браузер отрисовывает страницы в режиме совместимости с IE. При работе на сайтах интрасети может потребоваться метатег для переопределения поведения браузера по умолчанию.

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="feedback"></a>Отзывы

Если у вас возникли проблемы, сообщите об этом на [форумах Reporting Services](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices).

## <a name="see-also"></a>См. также раздел

[Интеграция служб Reporting Services с помощью элементов управления ReportViewer — сбор данных](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)


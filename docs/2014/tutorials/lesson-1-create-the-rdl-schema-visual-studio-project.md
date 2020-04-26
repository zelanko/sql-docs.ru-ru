---
title: Занятие 1. Создание проекта RDL-схемы Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c34062acefc2dfd847790a39cea35b03727f49ff
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62678522"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a>Урок 1. Создание проекта схемы языка определения отчетов в Visual Studio
  В этом учебнике будет создано простое приложение командной строки. В этом учебнике предполагается, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]что вы разрабатываете в.  
  
> [!NOTE]  
>  Чтобы обращаться к веб-службе сервера отчетов, работающей на сервере [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] с дополнительными службами, необходимо добавить «_SQLExpress» к пути «ReportServer». Пример:  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a>Создание учетной записи-посредника веб-службы  
  
1.  Выберите **Пуск** , **Все программы**, Microsoft Visual Studio 2010, а затем **Средства Visual Studio**и **Командная строка Visual Studio 2010**.  
  
2.  Если используется C#, в окне командной строки выполните следующую команду:  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Если используется Visual Basic, выполните следующую команду:  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Команда создаст файл с расширением CS или VB. Этот файл следует добавить к приложению.  
  
### <a name="to-create-a-console-application"></a>Создание приложения командной строки  
  
1.  В меню **Файл** выберите **Создать**, а затем **Проект** , чтобы открыть диалоговое окно **Новый проект** .  
  
2.  В панели слева в разделе **Установленные шаблоны**щелкните узел **Visual Basic** или **Visual C#** и выберите категорию типов проекта из раскрывшегося списка.  
  
3.  Выберите тип проекта **Консольное приложение** .  
  
4.  В поле **Name** введите имя проекта. Введите имя `SampleRDLSchema`.  
  
5.  В поле **Расположение** введите путь, по которому будет сохранен проект, или нажмите кнопку **Обзор** , чтобы перейти в эту папку.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]В обозреватель решений отображается свернутое представление проекта.  
  
7.  В меню **Проект** выберите пункт **Добавить существующий элемент**.  
  
8.  Перейдите в папку, где находится созданный файл CS или VB, выберите файл и нажмите кнопку **Добавить**.  
  
     Также для обеспечения работоспособности веб-ссылки необходимо добавить ссылку на пространство имен <xref:System.Web.Services>.  
  
9. В меню «Проект» выберите пункт **Добавить ссылку**.  
  
     В диалоговом окне **Добавить ссылку** на вкладке **.NET** выберите **System.Web.Services**и нажмите кнопку **ОК**.  
  
     Дополнительные сведения о подключении к веб-службе сервера отчетов см. в разделе [Создание приложений с помощью веб-службы и .NET Framework](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
10. Раскройте узел проекта в обозревателе решений. К проекту будет добавлен файл кода с именем по умолчанию Program.cs (Module1.vb для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
11. Откройте файл Program.cs (Module1.vb для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) и замените код следующим.  
  
     Следующий код обеспечивает заглушки методов, которые будут использоваться для выполнения функций загрузки, обновления и сохранения.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a>Следующее занятие  
 На следующем занятии предстоит использовать программу определения XML-схемы (Xsd.exe) для формирования классов из RDL-схемы и включения их в проект. См. [Lesson 2: Generate Classes from the RDL Schema using the xsd Tool](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md).  
  
## <a name="see-also"></a>См. также  
 [Обновление отчетов с использованием классов, созданных из учебника по схеме языка определения отчетов &#40;SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Язык определения отчетов (службы SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  

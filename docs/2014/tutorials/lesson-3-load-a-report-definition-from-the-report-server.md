---
title: Урок 3. Загрузка определения отчета с сервера отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d4c51002c8c829417c63a0dd6c59a3538604fd81
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042520"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a>Урок 3. Загрузка определения отчета с сервера отчетов
  После создания проекта и формирования классов из схемы языка определения отчетов необходимо загрузить определение отчета с сервера отчетов.  
  
### <a name="to-load-a-report-definition"></a>Загрузка определения отчета  
  
1.  Добавьте закрытое поле в верхней части `ReportUpdater` класс (модуля, если вы используете [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) для `Report` класса. Это поле будет использоваться для хранения ссылки на отчет, который загружается с сервера отчетов во время выполнения приложения.  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  Замените код метода `LoadReportDefinition()` в файле Program.cs (Module1.vb для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) следующим кодом.  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report definition   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report definition   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>Следующее занятие  
 На следующем занятии будет создан код для обновления определения отчета, которое было загружено с сервера отчетов. См. [Занятие 4. Обновление определения отчета программным способом](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).  
  
## <a name="see-also"></a>См. также  
 [Обновление отчетов с помощью классов, созданных из RDL-схемы &#40;учебник по службам SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Язык определения отчетов (службы SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  

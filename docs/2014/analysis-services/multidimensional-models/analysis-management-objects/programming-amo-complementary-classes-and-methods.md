---
title: Программирование дополнительных классов AMO и методов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- restores [AMO]
- assemblies [AMO]
- AMO, backup and restore
- capture logs [AMO]
- programming [AMO]
- Analysis Management Objects, backup and restore
- traces [AMO]
- backups [AMO]
ms.assetid: 14aed554-d2e2-49e5-9c72-26660759bce2
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 66fcd0c30acb2ddf62288cb549b96b74ebf7f7b9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317334"
---
# <a name="programming-amo-complementary-classes-and-methods"></a>Программирование дополнительных классов и методов объектов AMO
  Этот раздел состоит из следующих подразделов.  
  
-   [Класс Assembly](#Assembly)  
  
-   [Резервное копирование и восстановление](#BU)  
  
-   [Класс Trace](#TRC)  
  
-   [Класс CaptureLog и атрибут CaptureXML](#CL)  
  
##  <a name="Assembly"></a> Класс Assembly  
 Сборки позволяют пользователю расширять функциональные возможности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] путем добавления новых хранимых процедур или функций многомерных выражений (MDX). Дополнительные сведения см. в разделе [AMO другие классы и методы](amo-other-classes-and-methods.md).  
  
 Добавление и удаление сборок является простой операцией, и ее можно выполнить в режиме в сети. Чтобы добавить сборку в базу данных, пользователь должен быть либо администратором базы данных, либо администратором сервера (чтобы иметь возможность добавить сборку к объекту сервера).  
  
 В следующем образце сборка добавляется в указанную базу данных и задается учетная запись службы для ее выполнения. Если такая сборка уже существует в базе данных, то перед добавлением она будет удалена.  
  
```  
static public void CreateStoredProcedures(Database db)  
{  
    ClrAssembly clrAssembly;  
  
    // Verify That assembly exist in database and drop it  
    if (db.Assemblies.ContainsName("StoredProcedures"))  
    {  
        clrAssembly = db.Assemblies.FindByName("StoredProcedures");  
        clrAssembly.Drop();  
    }  
  
    // Create the CLR assembly  
    clrAssembly = db.Assemblies.Add("StoredProcedures");  
    clrAssembly.ImpersonationInfo = new ImpersonationInfo(  
        ImpersonationMode.ImpersonateServiceAccount);  
    clrAssembly.PermissionSet = PermissionSet.Unrestricted;  
  
    // Load the assembly files  
    clrAssembly.LoadFiles(Environment.CurrentDirectory  
        + @"\StoredProcedures2.dll", false);  
  
    clrAssembly.Update();  
}  
  
```  
  
##  <a name="BU"></a> Методы BACKUP и Restore  
 Методы Backup и Restore позволяют администраторам создавать резервные копии базы данных и производить ее восстановление.  
  
 В следующем образце создаются резервные копии всех баз данных на указанном сервере. Если файл резервной копии уже существует, то он будет перезаписан. Файлы резервных копий сохраняются в папке BackUp, которая вложена в папку данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
```  
static public void BackUpAllDatabases(Server svr)  
{  
    string fileName;  
    if ((svr != null) && ( svr.Connected))  
        foreach (Database db in svr.Databases)  
        {  
            fileName = db.Name + "_" + ((Int64)(DateTime.Today.Year * 10000 + DateTime.Today.Month * 100 + DateTime.Today.Day)).ToString()+ ".abf";  
            db.Backup(fileName, true);  
        }  
}  
```  
  
 В следующем образце производится восстановление базы данных Adventure Works из резервной копии, созданной в предыдущем образце. Если база данных My Adventure WorksDW уже существует, то она будет перезаписана.  
  
```  
static public void RestoreAdventureWorks(Server svr)  
{  
    svr.Restore("Adventure Works DW_20051025.abf", "My Adventure WorksDW", true);  
}  
```  
  
##  <a name="TRC"></a> Класс Trace  
 Для наблюдения за работой сервера необходимы два вида трассировок: трассировки сеансов и трассировки сервера. Трассировка сервера позволяет узнать ход выполнения текущей задачи на сервере (трассировки сеанса); трассировки также могут показать общую активность сервера в целом, при этом соединение с сервером даже не требуется (трассировки сервера).  
  
 При трассировке текущих действий (трассировки сеанса) сервер отправляет текущему приложению уведомления о происходящих на нем событиях, вызванных этим приложением. В текущем приложении события захватываются с помощью обработчиков событий. Сначала объекту <xref:Microsoft.AnalysisServices.SessionTrace> назначаются процедуры обработки событий, а затем запускается трассировка сеанса.  
  
 В следующем образце показано, как настроить трассировку сеанса для отслеживания текущих действий. Процедуры обработки событий находятся в конце образца, они выведут все сведения трассировки в объект System.Console. Чтобы сформировать события трассировки, после начала трассировки будет выполнена полная обработка образца куба Adventure Works.  
  
```  
static public void TestSessionTraces(Server svr)  
{  
    // Start the default trace  
  
    svr.SessionTrace.OnEvent  
        += new TraceEventHandler(DefaultTrace_OnEvent);  
    svr.SessionTrace.Stopped  
        += new TraceStoppedEventHandler(DefaultTrace_Stopped);  
    svr.SessionTrace.Start();  
  
    // Process the databases  
    // The trace handlers will output all progress notifications   
    // to the console  
    Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
    Cube cube = db.Cubes.FindByName("Adventure Works");  
    cube.Process(ProcessType.ProcessFull);  
  
    // Stop the default trace  
    svr.SessionTrace.Stop();  
  
}  
static public void DefaultTrace_OnEvent(object sender, TraceEventArgs e)  
{  
    Console.WriteLine("{0}", e.TextData);  
}  
  
static public void DefaultTrace_Stopped(ITrace sender, TraceStoppedEventArgs e)  
{  
    switch (e.StopCause)  
    {  
        case TraceStopCause.StoppedByUser:  
        case TraceStopCause.Finished:  
            Console.WriteLine("Processing completed successfully");  
            break;  
  
        case TraceStopCause.StoppedByException:  
            Console.WriteLine("Processing failed: {0}",  
                e.Exception.Message);  
            break;  
    }  
}  
```  
  
 Трассировка сервера может быть настроена таким образом, чтобы она записывала все данные в файл трассировки и автоматически перезапускалась при перезагрузке сервера.  
  
 Чтобы настроить трассировку сервера, сначала необходимо определить события, за которыми необходимо наблюдение, а также данные событий, которые следует сохранять в файле трассировки. Для каждого события необходимо определить столбцы данных, которые будут сохраняться в файле трассировки.  
  
 Создание трассировки сервера состоит из четырех шагов.  
  
1.  Создайте объект трассировки сервера и заполните его основные атрибуты.  
  
     Атрибут LogFileSize определяет максимальный размер файла трассировки, его значение задается в мегабайтах. Атрибут LogFileRollOver позволяет создавать другой файл журнала по достижении ограничения, установленного атрибутом LogFileSize. Когда этот параметр включен, к имени нового файла добавляется порядковый номер. Атрибут AutoRestart позволяет трассировке снова запускаться в случае перезапуска службы.  
  
2.  Создайте события и соответствующие столбцы данных.  
  
3.  По необходимости запускайте и останавливайте трассировку.  
  
     Даже после остановки трассировка сохраняется на сервере. Она должна запуститься снова, если в ней задано AutoRestart=`true`.  
  
4.  Удалите трассировку, когда она больше не нужна.  
  
 Взгляните на следующий образец. Если трассировка уже существует, то она удаляется, а затем создается повторно. Файлы трассировки сохраняются в папке Log, расположенной в папке данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
```  
static public void TestServerTraces(Server svr)  
{  
    Trace trc;  
    TraceEvent te;  
  
        trc = svr.Traces.FindByName("TestServerTraces");  
        if (trc != null)  
            trc.Drop();  
        trc = svr.Traces.Add("TestServerTraces", "TestServerTraces");  
        trc.LogFileName = ("TestServerTraces_" +((Int64)(DateTime.Now.Year * 10000 + DateTime.Now.Month * 100 + DateTime.Now.Day)).ToString() + "_" +  
                ((Int64)(DateTime.Now.Hour * 10000 + DateTime.Now.Minute * 100 + DateTime.Now.Second)).ToString() + ".trc");  
        trc.LogFileSize = 100;  
        trc.LogFileRollover = true;  
        trc.AutoRestart = false;  
  
        #region Define Events to trace & data columns per event  
        te = trc.Events.Add(TraceEventClass.ProgressReportBegin);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportCurrent);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportEnd);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.EndTime);  
        te.Columns.Add(TraceColumn.Success);  
        te.Columns.Add(TraceColumn.Error);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
        #endregion  
  
        trc.Update();  
        trc.Start();  
  
        #region Process the Adventure Works Cube  
        // The trace settings will output all progress notifications   
        // to the trace file  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        Cube cube = db.Cubes.FindByName("Adventure Works");  
        cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        trc.Stop();  
        trc.Drop();  
  
}  
```  
  
##  <a name="CL"></a> Атрибуты CaptureLog и CaptureXml  
 Атрибут CaptureLog позволяет создавать пакетные файлы XML для аналитики, содержащие операции AMO. Атрибут CaptureLog позволяет описывать в скрипте объекты сервера как базы данных, кубов, измерений, структур интеллектуального анализа и др.  
  
 Создание атрибута CaptureLog включает следующие шаги.  
  
1.  Запустите регистрацию событий в журнал XML для аналитики, установив атрибут CaptureXml в значение `true`.  
  
     После установки этого параметра все операции AMO сохраняются в коллекции строк, а не отправляются на сервер.  
  
2.  Запустите работу объектов AMO как обычно, но помните, что ни одно действие на сервер отправлено не будет. Работа может состоять из любой операции: обработки, создания, удаления, обновления или любого другого действия с объектом.  
  
3.  Остановите запись событий в журнал XML для аналитики, установив атрибут CaptureXml в значение `false`.  
  
4.  Просмотрите записанные данные XML для аналитики либо в строках коллекции CaptureLog, либо сформировав полную строку с помощью метода ConcatenateCaptureLog. Метод ConcatenateCaptureLog позволяет формировать пакеты XMLA в форме одной транзакции, а также добавлять в пакет параметр параллельной обработки.  
  
 Следующий образец возвращает строку с пакетом команд для выполнения полной обработки всех измерений и всех кубов базы данных [Adventure Works DW Multidimensional 2012].  
  
```  
static public string TestCaptureLog(Server svr)  
{  
    String capturedXmla = "";  
    if ((svr != null) && (svr.Connected))  
    {  
        svr.CaptureXml = true;  
  
        #region Actions to be captured to an XMLA file  
        //No action is executed during CaptureXml = true  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        foreach (Dimension dim in db.Dimensions)  
            dim.Process(ProcessType.ProcessFull);  
        foreach (Cube cube in db.Cubes)  
            cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        svr.CaptureXml = false;  
  
        capturedXmla = svr.ConcatenateCaptureLog(true, true);  
  
    }  
  
    return capturedXmla;  
}  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices>   
 [Введение в классы объектов AMO](amo-classes-introduction.md)   
 [Объекты AMO другие классы и методы](amo-other-classes-and-methods.md)   
 [Логическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40;службы Analysis Services — многомерные данные&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Обработка объектов многомерной модели](../processing-a-multidimensional-model-analysis-services.md)  
  
  

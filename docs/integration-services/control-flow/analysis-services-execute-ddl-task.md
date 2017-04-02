---
title: "Задача &#171;Выполнение инструкции DDL служб Analysis Services&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asexecuteddltask.f1"
helpviewer_keywords: 
  - "задача «Выполнение инструкции DDL служб Analysis Services»"
  - "DDL"
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 48
---
# Задача &#171;Выполнение инструкции DDL служб Analysis Services&#187;
  задача «Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]» запускает инструкции языка DDL, которые могут создавать, удалять или изменять модели интеллектуального анализа данных и многомерные объекты, такие как кубы и измерения. Например, инструкция DDL позволяет создать секцию в кубе **Adventure Works** или удалить измерение в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], образце базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входящем в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Задача «Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или к проекту [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в статье [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат ряд задач, выполняющих операции бизнес-аналитики, таких как обработка аналитических объектов и запуск запросов прогнозирования интеллектуального анализа данных.  
  
 Дополнительные сведения о задачах, связанных с бизнес-аналитикой, см. в следующих разделах:  
  
-   [Задача «Обработка средствами Analysis Services»](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [Задача «Запрос интеллектуального анализа данных»](../../integration-services/control-flow/data-mining-query-task.md)  
  
## Инструкции DDL  
 Инструкции DDL представлены как инструкции в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) и встроены в команду XML для аналитики (XMLA).  
  
-   ASSL используется для определения и описания экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , базы данных и объектов базы данных, которые он содержит. Дополнительные сведения см. в разделе [Справочник по языку ASSL](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
-   XML для аналитики — это язык команд, используемый для отправки команд-действий, таких как «Создать», «Изменить» или «Обработать», экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения см. в разделе [Справочник по XML для аналитики (XMLA)](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md).  
  
 Если DDL-код хранится в отдельном файле, задача «Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » использует диспетчер подключения файлов для указания пути файла. Дополнительные сведения см. в статье [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
 Так как инструкции DDL могут содержать пароли и другие важные сведения, пакет, содержащий одну или несколько задач "Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]", должен использовать уровень защиты пакета **EncryptAllWithUserKey** или **EncryptAllWithPassword**. Дополнительные сведения см. в разделе [Пакеты служб Integration Services (SSIS)](../../integration-services/integration-services-ssis-packages.md).  
  
### Примеры DDL  
 Следующие три инструкции DDL были сформированы объектами сценария в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входящей в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Следующая инструкция DDL удаляет измерение **Promotion** .  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 Следующая инструкция DDL обрабатывает куб [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] .  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 Следующая инструкция DDL создает модель интеллектуального анализа данных **Forecasting** .  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 Следующие три инструкции DDL были сформированы объектами сценария в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входящей в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Следующая инструкция DDL удаляет измерение **Promotion** .  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 Следующая инструкция DDL обрабатывает куб [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] .  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 Следующая инструкция DDL создает модель интеллектуального анализа данных **Forecasting** .  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## Настройка задачи «Выполнение инструкции DDL служб Analysis Services»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор задачи "Выполнение инструкции DDL служб Analysis Services" (страница "Общие")](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-general-page.md)  
  
-   [Редактор задачи "Выполнение инструкции DDL служб Analysis Services" (страница "DDL")](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-ddl-page.md)  
  
-   [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Программная настройка задачи «Выполнение инструкции DDL служб Analysis Services»  
 Дополнительные сведения об установке этих свойств программными средствами см. в следующем разделе.  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  
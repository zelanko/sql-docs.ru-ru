---
description: Задача «Выполнение инструкции DDL служб Analysis Services»
title: Задача "Выполнение инструкции DDL служб Analysis Services" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.asexecuteddltask.f1
- sql13.dts.designer.asexecuteddltask.general.f1
- sql13.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL task
- DDL
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2496345f217f61f3729a6bf657a882e045cc130b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88350000"
---
# <a name="analysis-services-execute-ddl-task"></a>Задача «Выполнение инструкции DDL служб Analysis Services»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  задача «Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » запускает инструкции языка DDL, которые могут создавать, удалять или изменять модели интеллектуального анализа данных и многомерные объекты, такие как кубы и измерения. Например, инструкция DDL позволяет создать секцию в кубе **Adventure Works** или удалить измерение в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], образце базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входящем в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Задача «Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для подключения к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или к проекту [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в статье [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат ряд задач, выполняющих операции бизнес-аналитики, таких как обработка аналитических объектов и запуск запросов прогнозирования интеллектуального анализа данных.  
  
 Дополнительные сведения о задачах, связанных с бизнес-аналитикой, см. в следующих разделах:  
  
-   [Задача «Обработка средствами Analysis Services»](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [Задача «Запрос интеллектуального анализа данных»](../../integration-services/control-flow/data-mining-query-task.md)  
  
## <a name="ddl-statements"></a>Инструкции DDL  
 Инструкции DDL представлены как инструкции в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) и встроены в команду XML для аналитики (XMLA).  
  
-   ASSL используется для определения и описания экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , базы данных и объектов базы данных, которые он содержит. Дополнительные сведения см. в разделе [Справочник по языку ASSL](https://docs.microsoft.com/analysis-services/assl/analysis-services-scripting-language-assl-for-xmla).  
  
-   XML для аналитики — это язык команд, используемый для отправки команд-действий, таких как «Создать», «Изменить» или «Обработать», экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения см. в разделе [Справочник по XML для аналитики (XMLA)](https://docs.microsoft.com/analysis-services/xmla/xml-for-analysis-xmla-reference).  
  
 Если DDL-код хранится в отдельном файле, задача «Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] » использует диспетчер подключения файлов для указания пути файла. Дополнительные сведения см. в статье [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
 Так как инструкции DDL могут содержать пароли и другие важные сведения, пакет, содержащий одну или несколько задач "Выполнение инструкции DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]", должен использовать уровень защиты пакета **EncryptAllWithUserKey** или **EncryptAllWithPassword**. Дополнительные сведения см. в разделе [Пакеты служб Integration Services (SSIS)](../../integration-services/integration-services-ssis-packages.md).  
  
### <a name="ddl-examples"></a>Примеры DDL  
 Следующие три инструкции DDL были сформированы объектами сценария в [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входящей в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Следующая инструкция DDL удаляет измерение **Promotion** .  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 Следующая инструкция DDL обрабатывает куб [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] .  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 Следующая инструкция DDL обрабатывает куб [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] .  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
## <a name="configuration-of-the-analysis-services-execute-ddl-task"></a>Настройка задачи «Выполнение инструкции DDL служб Analysis Services»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="programmatic-configuration-of-the-analysis-services-execute-ddl-task"></a>Программная настройка задачи «Выполнение инструкции DDL служб Analysis Services»  
 Дополнительные сведения об установке этих свойств программными средствами см. в следующем разделе.  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
## <a name="analysis-services-execute-ddl-task-editor-general-page"></a>Редактор задачи «Выполнение инструкции DDL служб Analysis Services» (страница «Общие»)
  Используйте страницу **Общие** диалогового окна **Редактор задачи " Выполнение инструкции DDL служб Analysis Services"** для назначения имени и описания задания выполнения DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
### <a name="options"></a>Параметры  
 **имя**;  
 Задает уникальное имя задаче Execute DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Предоставляет описание задачи Execute DDL служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>Редактор задачи «Выполнение инструкции DDL служб Analysis Services» (страница DDL)
  Используйте страницу **DDL** диалогового окна **Редактор задачи "Выполнение инструкции DDL служб аналитики"** , чтобы настроить соединение с проектом [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или базой данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а также предоставить сведения об источнике инструкций языка определения данных (DDL).  
  
### <a name="static-options"></a>Статические параметры  
 **Соединение**  
 Выберите проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или диспетчер подключений [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в списке или щелкните \<**New connection...**> и создайте подключение с помощью диалогового окна **Добавление диспетчера соединений со службами Analysis Services**.  
  
 **См. также:** [Диалоговое окно "Добавление диспетчера соединений со службами Analysis Services" в справочнике по пользовательскому интерфейсу](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Диспетчер соединений служб Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)  
  
 **Тип источника**  
 Указать тип источника инструкции DDL. Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Прямой ввод**|Установите в качестве источника инструкцию DDL, содержащуюся в текстовом поле **SourceDirect** . При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Соединение с файлом**|В качестве источника указывается файл, содержащий инструкцию DDL. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
|**Переменная**|Установите в качестве источника переменную. При выборе этого значения в следующем подразделе отображаются динамические параметры.|  
  
### <a name="dynamic-options"></a>Динамические параметры  
  
#### <a name="sourcetype--direct-input"></a>SourceType = Прямой ввод  
 **Source**  
 Введите инструкции DDL или нажмите кнопку с многоточием **(…)** и после этого введите инструкции в диалоговом окне **Инструкции DDL**.  
  
#### <a name="sourcetype--file-connection"></a>SourceType = Подключение файла  
 **Source**  
 Выберите "Соединение с файлом" в списке или щелкните \<**New connection...**> и создайте подключение с помощью диалогового окна **Диспетчер соединения файлов**.  
  
 **См. также:** [Диспетчер соединения файлов](../../integration-services/connection-manager/file-connection-manager.md)  
  
#### <a name="sourcetype--variable"></a>SourceType = Переменная  
 **Source**  
 Выберите переменную в списке или щелкните \<**New variable...**> и создайте переменную с помощью диалогового окна **Добавление переменной**.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md)  
  

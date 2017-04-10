---
title: "Открытие проектов служб Integration Services в клиенте DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Открытие проектов служб Integration Services в клиенте DQS
  Компонента очистки DQs в службах Integration Services позволяет запускать проект очистки в пакетном режиме. Однако в некоторых случаях может потребоваться просмотреть результаты очистки в пакете служб Integration Services, аналогично как можно просмотреть результаты очистки в **Управление и просмотр результатов** вкладку операции очистки в проекте качества данных в DQS. DQS позволяет открывать проекты служб Integration Services в [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] так же, как проект качества данных из **Открыть проект** экрана и интерактивной очистки среды результаты очистки в проекте служб Integration Services.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="LimitationsRestrictions"></a> Ограничения  
  
-   Только завершенные проекты доступны в службы Integration Services **Открыть проект** экрана в [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Сбой или выполняемые проекты недоступны в **Открыть проект** экрана.  
  
-   Открытие проектов служб Integration Services на этапе интерактивной очистки (**Просмотр и управление ими результаты** Вкладка) в [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Не удается перейти к **Очистка** или **карты** вкладок. Вы можете перейти только на **экспортировать** нажав кнопку **Далее**.  
  
-   Нельзя удалить заблокированный проект служб Integration Services из [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Чтобы проект можно было удалить, его необходимо сначала разблокировать.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Вы должны успешно завершить выполняемый проект служб Integration Services, содержащей пакет с помощью компонента очистки DQS в разделе и открыть его в [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для управления проектом служб Integration Services необходимо иметь роль dqs_kb_editor или dqs_kb_operator в базе данных DQS_MAIN.  
  
  
##  <a name="Open"></a> Открытие проекта служб Integration Services  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запустите клиентское приложение DQS](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  В [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] главной, нажмите кнопку **Открыть проект качества данных**. Появится экран **Открытие проекта** .  
  
3.  В **Открыть проект** экрана, можно определить проект служб Integration Services одним из следующих способов:  
  
    1.  **Имя проекта**: проекты служб Integration Services перечислены с использованием следующей терминологии: «Package.DQS Cleansing_*\< Дата>**\< время>*_ {GUID}.» Каждый раз при успешном выполнении того же пакета [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], новый проект отображается в **Открыть проект** экрана.  
  
    2.  **Тип проекта**: проекты служб Integration Services имеют **SSIS** проекта в качестве типа **Открыть проект** экрана.  
  
     Выберите проект и нажмите кнопку **Далее**.  
  
4.  Откроется проект служб Integration Services на этапе интерактивной очистки (**Просмотр и управление ими результаты** вкладке). Вы можете выполнить интерактивную очистку данных в проекте служб Integration Services. Дополнительные сведения о **Управление и просмотр результатов** см. в разделе [этап интерактивной очистки](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) в [очистки данных с помощью DQS &#40; внутренний &#41; Базы знаний](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).  
  
5.  Щелкните **Далее** Чтобы перейти к **Экспорт** вкладки, где можно экспортировать обработанные данные в любой из следующих: новую таблицу в базе данных SQL Server, CSV-файла или файла Excel. Дополнительные сведения о **Экспорт** см. в разделе [этап экспорта](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) в [очистки данных с помощью DQS &#40; внутренний &#41; Базы знаний](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
6.  После экспорта данных, нажмите кнопку **Готово** Закрыть проект служб Integration Services.  

  
## См. также:  
 [Преобразование «Очистка DQS»](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Службы Integration Services (SSIS) проектов](https://msdn.microsoft.com/library/ms138028.aspx)  
  
  
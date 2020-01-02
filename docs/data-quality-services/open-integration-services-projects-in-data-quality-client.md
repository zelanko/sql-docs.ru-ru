---
title: Открытие проектов Integration Services (SSIS) в Data Quality Client
description: Узнайте, как открыть проект SQL Server Integration Services (SSIS) с помощью Data Quality Client для SQL Server Data Quality Services.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
author: swinarko
ms.author: sawinark
ms.openlocfilehash: a070f5a279cdddfb78d3188c210faf43661d5516
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75557849"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a>Открытие проектов служб Integration Services в клиенте DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Компонент очистки DQS в Integration Services позволяет запускать проект очистки в пакетном режиме. Но иногда полезно просмотреть результаты очистки в пакете служб Integration Services, подобно тому, как вы можете просмотреть результаты очистки на вкладке **Просмотр результатов и управление ими** операции очистки в проекте служб DQS. Службы DQS позволяют открывать проекты служб Integration Services в [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] точно так же, как любой другой проект служб DQS, с экрана **Открытие проекта** и интерактивно обрабатывать результаты очистки в проекте служб Integration Services.  
  
##  <a name="BeforeYouBegin"></a>Перед началом  
  
###  <a name="LimitationsRestrictions"></a>Ограничения  
  
-   На экране **Открытие проекта** в клиенте [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]доступны только завершенные проекты служб Integration Services. Завершившиеся с ошибкой или выполняемые проекты недоступны на экране **Открытие проекта** .  
  
-   Проекты служб Integration Services открываются на этапе интерактивной очистки (вкладка**Просмотр результатов и управление ими** ) в клиенте [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Нельзя перейти на вкладки **Очистка** или **Сопоставление** . Вы можете перейти только на вкладку **Экспорт** , нажав кнопку **Далее**.  
  
-   Нельзя удалить заблокированный проект служб Integration Services из [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Чтобы проект можно было удалить, его необходимо сначала разблокировать.  
  
###  <a name="Prerequisites"></a>Требований  
 Необходимо успешно завершить выполняемый проект служб Integration Services, содержащий проект с компонентом DQS Cleansing, чтобы просмотреть и открыть его в [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
###  <a name="Security"></a>Бюллетеня  
  
####  <a name="Permissions"></a>Чтение  
 Для управления проектом служб Integration Services необходимо иметь роль dqs_kb_editor или dqs_kb_operator в базе данных DQS_MAIN.  
  
  
##  <a name="Open"></a>Открытие проекта Integration Services  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] главном экране щелкните **Open Data Quality Project (открыть проект**служб DQS). Появится экран **Открытие проекта** .  
  
3.  На экране **Открытие проекта** проект служб Integration Services вы можете определить любым из следующих способов:  
  
    1.  **Имя проекта**: Integration Services проекты перечислены с использованием следующей терминологии именования: "Package. DQS Cleansing_*\<Дата \<>время>*_ {GUID}". При каждом успешном выполнении того же пакета в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]новый пакет появляется на экране **Открытие проекта** .  
  
    2.  **Тип проекта**: Integration Services проекты имеют тип проекта **SSIS** на экране **Открытие проекта** .  
  
     Выберите проект и нажмите кнопку **Далее**.  
  
4.  Проект служб Integration Services открывается на интерактивном этапе очистки (вкладка**Просмотр результатов и управление ими** ). Вы можете выполнить интерактивную очистку данных в проекте служб Integration Services. Подробные сведения о вкладке **Управление и просмотр результатов** см. в разделе [Этап интерактивной очистки](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) статьи [Очистка данных с использованием набора знаний служб DQS &#40;внутренних&#41;](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).  
  
5.  Щелкните **Далее** чтобы открыть вкладку **Экспорт** , на которой можно экспортировать обработанные данные в одно из этих расположений: новая таблица в базе данных SQL Server, CSV-файл или файл Excel. Подробные сведения о вкладке **Экспорт** см. в разделе [Этап экспорта](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) статьи [Очистка данных с использованием набора знаний служб DQS &#40;внутренних&#41;](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
6.  После экспорта данных нажмите кнопку **Готово** , чтобы закрыть проект служб Integration Services.  

  
## <a name="see-also"></a>См. также  
 [Преобразование «Очистка DQS»](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)   
 [Проекты Integration Services (SSIS)](../integration-services/integration-services-ssis-projects-and-solutions.md)  
  
  

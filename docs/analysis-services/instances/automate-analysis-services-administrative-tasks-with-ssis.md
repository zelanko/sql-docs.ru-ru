---
title: Автоматизировать административные задачи служб Analysis Services с помощью служб SSIS | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c750c0e8ee9f13c4b4751af872b02f4ed9ee419a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659597"
---
# <a name="automate-analysis-services-administrative-tasks-with-ssis"></a>Автоматизация административных задач служб Analysis Services с помощью служб SSIS
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяют автоматизировать выполнение скриптов DDL, задач по обработке кубов и моделей интеллектуального анализа данных, а также задач запросов интеллектуального анализа данных. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно рассматривать как набор задач потока управления и задач по обслуживанию, которые можно соединять, образуя последовательные и параллельные задания по обработке данных.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предназначены для выполнения операций очистки данных во время выполнения задач обработки данных и для объединения данных из различных источников данных. При работе с кубами и моделями интеллектуального анализа данных службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут преобразовывать нечисловые данные в числовые и могут гарантировать, что значения типа данных содержатся в ожидаемых пределах, тем самым создавая достоверные данные, которыми производится заполнение таблиц фактов и измерений.  
  
## <a name="integration-services-tasks"></a>Задачи служб Integration Services  
 Любая задача или задание служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] состоит из элементов двух основных типов: элементов потока управления и элементов потока данных. Элементы потока управления определяют логическое упорядочивание выполнения задания путем применения ограничений очередностью. Элементы потока данных относятся к соединению между выходом компонента и входом следующего компонента, а также к любому преобразованию данных, которое может применяться к переходным данным. В отношении решений об отправке данных различным компонентам ограничения очередностью содержат логику, указывающую, какой компонент получает выход. Задачи служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , наиболее важные для служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , включают задачу выполнения DDL, задачу обработки средствами Analysis Services и задачу запроса интеллектуального анализа данных. Для каждой из этих задач может использоваться задача отправки почты для отправки администратору сообщения электронной почты, содержащего результаты выполнения задачи.  
  
## <a name="the-execute-ddl-task"></a>Задача выполнения DDL  
 Задача выполнения DDL в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяет отправлять скрипты DDL непосредственно серверу служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и запускать их автоматически. Это позволяет администратору служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполнять операции создания резервных копий, восстановления и синхронизации из пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Пакет состоит из элементов потоков данных и управления, описанных ранее, которые должны быть **run regularly**, как и другие инструкции DDL, которые можно добавлять к задачам. Поскольку обсуждаемые здесь задачи часто запускаются ночью, особенно полезно иметь пакеты, которые можно легко запускать из любого приложения планирования. Можно запланировать запуск пакета в любое время, используя агент служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Дополнительные сведения о реализации этой задачи см. в разделе [Задача "Выполнение DDL службами Analysis Services"](../../integration-services/control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="analysis-services-processing-task"></a>задача «Обработка средствами Analysis Services»  
 Задача «Обработка средствами Analysis Services» в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяет автоматически заполнять кубы новыми данными при внесении периодических обновлений в исходную реляционную базу данных. Используя задачу «Обработка средствами Analysis Services», можно осуществлять обработку на уровне измерения, куба или секции. Сама обработка может иметь тип **incremental** или **full**, выбранный на основе требований к заданиям. При добавочной обработке добавляются новые данные и выполняется достаточное количество пересчетов, чтобы целевой объект содержал последние данные, в то время как при полной обработке существующие данные сбрасываются и выполняется полная перезагрузка и пересчет. Полная обработка занимает больше времени, но является более законченной. Дополнительные сведения о реализации этой задачи см. в разделе [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).  
  
## <a name="data-mining-query-task"></a>Задача «Запрос интеллектуального анализа данных»  
 Задача «Запрос интеллектуального анализа» в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяет извлекать и сохранять данные из моделей интеллектуального анализа данных. Эти данные часто хранятся в реляционной базе данных и могут использоваться, например для определения списка потенциальных заказчиков для целевой маркетинговой кампании. Интеллектуальный анализ данных может идентифицировать ценность заказчика и вероятность того, что этот заказчик ответит на конкретный маркетинговый ход. Задачу «Запрос интеллектуального анализа» можно использовать для извлечения и изменения данных в предпочтительном формате. Дополнительные сведения о реализации этой задачи см. в разделе [Data Mining Query Task](../../integration-services/control-flow/data-mining-query-task.md).  
  
## <a name="see-also"></a>См. также  
 [Назначение обработки секции](../../integration-services/data-flow/partition-processing-destination.md)   
 [Назначение «Обработка измерений»](../../integration-services/data-flow/dimension-processing-destination.md)   
 [Преобразование «Запрос интеллектуального анализа данных»](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)   
 [Обработка многомерной модели (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
  
  

---
title: "Шаг 1. Копирование пакета, созданного на занятии 4 | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
caps.latest.revision: "24"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9d7c64162898389439190286fa470854bc716318
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="lesson-5-1---copying-the-lesson-4-package"></a>Занятие 5-1. Копирование пакета, созданного на занятии 4
В этой задаче будет создана копия пакета Lesson 4.dtsx, созданного на занятии 4. Либо можно добавить пакет для занятия 4, прилагаемый к учебнику по проекту, и скопировать его. Полученная копия впоследствии будет использоваться на протяжении всего занятия 5.  
  
### <a name="to-copy-the-lesson-4-package"></a>Копирование пакета занятия 4  
  
1.  Если средства [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools еще не открыты, нажмите кнопку **Пуск**, наведите указатель на пункт **Все программы**, затем на пункт **Microsoft SQL Server 2012**и выберите пункт **SQL Server Data Tools**.  
  
2.  В меню **Файл** последовательно выберите пункты **Открыть**, **Проект или решение**, **Учебник по службам SSIS** и нажмите кнопку **Открыть**, а затем дважды щелкните файл **SSIS Tutorial.sln**.  
  
3.  В обозревателе решений правой кнопкой мыши щелкните **Lesson 4.dtsx**и выберите команду **Копировать**.  
  
4.  В обозревателе решений правой кнопкой мыши щелкните элемент **Пакеты служб SSIS**и выберите команду **Вставить**.  
  
    По умолчанию копируемому пакету присваивается имя Lesson 5.dtsx.  
  
5.  Чтобы открыть пакет, в обозревателе решений дважды щелкните **Lesson 5.dtsx** .  
  
6.  Щелкните правой кнопкой мыши фон вкладки **Поток управления** и выберите пункт **Свойства**.  
  
7.  В окне "Свойства" измените свойство **Name** на **Занятие 5**.  
  
8.  Установите флажок для свойства **ID** , щелкните стрелку раскрывающегося списка, а затем в списке выберите **<Generate New ID>**.  
  
### <a name="to-add-the-completed-lesson-4-package"></a>Добавление готового пакета занятия 4  
  
1.  Откройте [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools, затем откройте проект «Учебник по службам SSIS».  
  
2.  В обозревателе решений правой кнопкой мыши щелкните **Пакеты служб SSIS**и выберите команду **Добавить существующий пакет**.  
  
3.  В диалоговом окне **Добавление копии существующего пакета** в разделе **Расположение пакета**выберите пункт **Файловая система**.  
  
4.  Нажмите кнопку обзора **(…)** , перейдите в папку с пакетом **Lesson 4.dtsx** на компьютере и нажмите кнопку **Открыть**.  
  
    Чтобы загрузить все пакеты занятий этого учебника, выполните следующие действия.  
  
    1.  Перейдите к [образцам продуктов служб Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027).  
  
    2.  Перейдите на вкладку **DOWNLOADS** .  
  
    3.  Щелкните файл SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Скопируйте и вставьте пакет занятия 4, как описано в шагах 3–8 предыдущей процедуры.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Шаг 2. Активация и настройка конфигурации пакетов](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  

---
title: "Шаг 2. Создание проекта развертывания | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da96393429cf37224ef609b1ed1de52f41704015
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="lesson-1-2---creating-the-deployment-project"></a>Занятие 1–2. Создание проекта развертывания
В службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]развертываемый модуль находится в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Перед развертыванием пакетов нужно создать новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и добавить в него все пакеты и вспомогательные файлы, которые нужно развертывать вместе с пакетами.  
  
### <a name="to-create-the-integration-services-project"></a>Создание проекта служб Integration Services  
  
1.  Нажмите кнопку **Пуск**, наведите указатель на пункт **Все программы**, наведите указатель на пункт **Microsoft SQL Server**и выберите пункт **SQL Server Data Tools**.  
  
2.  В меню **Файл** наведите указатель на пункт **Создать**и выберите пункт **Проект** , чтобы создать проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  В диалоговом окне **Создание проекта** на панели **Шаблоны** выберите пункт **Проект служб SSIS** .  
  
4.  В поле **Имя** измените заданное по умолчанию имя на **Учебник по развертыванию**. При необходимости снимите флажок **Создать каталог для решения** .  
  
5.  Примите расположение по умолчанию или нажмите кнопку **Обзор** , чтобы выбрать папку.  
  
6.  В диалоговом окне **Расположение проекта** выберите папку и нажмите кнопку **Открыть**.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  По умолчанию будет создан пустой пакет с именем Package.dtsx, который будет добавлен к проекту. Однако вы не будете использовать этот пакет, вместо этого нужно добавить в проект существующий пакет. Поскольку будут развернуты все пакеты в проекте, следует удалить файл Package.dtsx. Чтобы удалить файл, щелкните его правой кнопкой мыши и выберите пункт **Удалить**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Шаг 3. Добавление пакетов и других файлов](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
## <a name="see-also"></a>См. также:  
[Проекты служб Integration Services (SSIS)](~/integration-services/integration-services-ssis-projects-and-solutions.md)  
  
  
  


---
title: 'Задача 4: Создание проекта служб SSIS, с помощью SQL Server Data Tools | Документы Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 03c0a6599990357a255fab3beeb434db3cb5d97d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189154"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Задача 4. Создание проекта служб SSIS с помощью SQL Server Data Tools
  В этой задаче создается проект служб SSIS с помощью **SQL Server Data Tools** для автоматизации очистки и сопоставления данных поставщика.  
  
1.  Запустите **SQL Server Data Tools**. Нажмите кнопку Пуск, выберите пункт **все программы**, разверните **Microsoft SQL Server 2012**и нажмите кнопку **SQL Server Data Tools**.  
  
2.  В меню **Файл** укажите пункт **Создать**, затем выберите пункт **Проект**.  
  
3.  Разверните **бизнес-аналитики** в **установленные шаблоны** и выберите **службы Integration Services**.  
  
     ![Visual Studio — диалоговое окно нового проекта](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio — диалоговое окно нового проекта")  
  
4.  Выберите **проект служб Integration Services** в **список типов проектов**.  
  
5.  Тип **CleanseAndCurateSuppliers** для **имя** и нажмите кнопку **ОК**.  
  
6.  В **обозревателе решений** окно, щелкните правой кнопкой мыши **Package.dtsx** и выберите **переименование**. Если вы не видите **обозревателе решений** окно, нажмите кнопку **представление** в строке меню щелкните **обозревателе решений**.  
  
     ![Package.dtsx — меню переименования](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx — меню переименования")  
  
7.  Тип **CleanseAndCurate.dtsx** и нажмите клавишу **ввод**. Убедитесь, что **расширения** остается **расширением dtsx**.  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 5. Добавление задачи потока данных](task-5-adding-data-flow-task.md)  
  
  
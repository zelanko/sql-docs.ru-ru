---
title: Задача 4. Создание проекта служб SSIS с помощью SQL Server Data Tools | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 8fb38cb068aca480756db7d962540137c8d4bfac
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65489206"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Задача 4. Создание проекта SSIS с помощью SQL Server Data Tools
  В этой задаче вы Создание проекта служб SSIS с помощью **SQL Server Data Tools** для автоматизации очистки и сопоставления данных поставщика.  
  
1.  Запустите **SQL Server Data Tools**. Нажмите кнопку Пуск, выберите пункт **все программы**, разверните **Microsoft SQL Server 2012**и нажмите кнопку **SQL Server Data Tools**.  
  
2.  В меню **Файл** укажите пункт **Создать**, затем выберите пункт **Проект**.  
  
3.  Разверните **бизнес-аналитики** в **установленные шаблоны** области и выберите **служб Integration Services**.  
  
     ![Visual Studio — диалоговое окно "новый проект"](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio — диалоговое окно \"новый проект\"")  
  
4.  Выберите **проект служб Integration Services** в **список типов проектов**.  
  
5.  Тип **CleanseAndCurateSuppliers** для **имя** и нажмите кнопку **ОК**.  
  
6.  В **обозревателе решений** окно, щелкните правой кнопкой мыши **Package.dtsx** и выберите **Переименовать**. Если вы не видите **обозревателе решений** окно, нажмите кнопку **представление** в строке меню щелкните **обозревателе решений**.  
  
     ![Package.dtsx — меню переименования](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx — меню переименования")  
  
7.  Тип **CleanseAndCurate.dtsx** и нажмите клавишу **ввод**. Убедитесь, что **расширение** остается **.dtsx**.  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 5. Добавление задачи потока данных](task-5-adding-data-flow-task.md)  
  
  

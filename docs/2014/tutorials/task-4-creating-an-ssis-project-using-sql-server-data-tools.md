---
title: Задача 4. Создание проекта служб SSIS с помощью SQL Server Data Tools | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 935409eeb7724f4c9807aecc8ec69c4cba0735a1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85006496"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Задача 4. Создание проекта SSIS с помощью SQL Server Data Tools
  В этой задаче вы создадите проект служб SSIS с помощью **SQL Server Data Tools** для автоматизации очистки и сопоставления данных поставщика.

1.  Запустите **SQL Server Data Tools**. Нажмите кнопку Пуск, укажите **все программы**, разверните **Microsoft SQL Server 2012**и щелкните **SQL Server Data Tools**.

2.  В меню **Файл** укажите пункт **Создать**, затем выберите пункт **Проект**.

3.  Разверните узел **Бизнес-аналитика** в области **Установленные шаблоны** и выберите **Integration Services**.

     ![Visual Studio — диалоговое окно «Создание проекта»](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio — диалоговое окно «Создание проекта»")

4.  Выберите **Integration Services проект** в **списке типов проектов**.

5.  Введите **CleanseAndCurateSuppliers** в качестве **имени** и нажмите кнопку **ОК**.

6.  В **Обозреватель решений** окне щелкните правой кнопкой мыши **Package. dtsx** и выберите команду **Переименовать**. Если окно **Обозреватель решений** не отображается, нажмите кнопку **Просмотр** в строке меню и выберите пункт **Обозреватель решений**.

     ![Package.dtsx — меню переименования](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx — меню переименования")

7.  Введите **CleanseAndCurate. dtsx** и нажмите клавишу **Ввод**. Убедитесь, что **расширение** остается в виде **dtsx**.

## <a name="next-step"></a>Следующий шаг
 [Задача 5. Добавление задачи потока данных](task-5-adding-data-flow-task.md)



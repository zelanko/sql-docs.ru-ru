---
title: Создание отчета Power View с многомерными источниками данных | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a34a67b5a963ba7c7adface2137a26e9194709d1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-power-view-report-with-a-multidimensional-data-source"></a>Создание отчета Power View с многомерными источниками данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Создание отчета Power View на основе многомерной модели не отличается от создания отчета на основе книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] или табличной модели служб Analysis Services. Отчеты Power View создаются из файла соединения с источником данных отчета (RSDS) в библиотеке SharePoint. Дополнительные сведения о создании RSDS см. в разделе [Create a Report Data Source](../../analysis-services/multidimensional-models/create-a-report-data-source.md).  
  
 Перед началом работы нужно знать следующее:  
  
-   Имя и расположение библиотеки SharePoint, содержащей общее соединение источника данных отчета (RSDS) с многомерной моделью.  
  
#### <a name="create-a-new-blank-power-view-report"></a>Создание нового пустого отчета Power View  
  
-   В библиотеке SharePoint щелкните стрелку рядом с общим соединением с источником данных отчета RSDS (RSDS-файл, который подключается к многомерной модели) и нажмите кнопку **Создать отчет Power View**.  
  
  

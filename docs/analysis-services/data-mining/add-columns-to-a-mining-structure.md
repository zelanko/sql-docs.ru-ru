---
title: "Добавить столбцы к структуре интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5dfeade08192456bae474b633af9bd401dfa0fde
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="add-columns-to-a-mining-structure"></a>добавить столбцы к структуре интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Используйте конструктор интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , чтобы добавить столбцы к структуре интеллектуального анализа данных после ее определения в мастере интеллектуального анализа данных. Можно добавить любой столбец, существующий в представлении источника данных, который использовался при определении структуры интеллектуального анализа данных.  
  
> [!NOTE]  
>  К структуре интеллектуального анализа данных можно добавить несколько копий столбцов. Тем не менее следует избегать использования более чем одного экземпляра столбца в одной и той же модели, поскольку в противном случае могут возникнуть ложные корреляции между исходным и производным столбцами.  
  
### <a name="to-add-a-column-to-a-mining-structure"></a>Добавление столбца к структуре интеллектуального анализа данных  
  
1.  Перейдите на вкладку **Структура интеллектуального анализа данных** в конструкторе интеллектуального анализа данных.  
  
2.  Щелкните правой кнопкой мыши структуру интеллектуального анализа данных и выберите пункт **Добавить столбец**.  
  
     Откроется диалоговое окно **Выбор столбца** .  
  
3.  В разделе **Исходная таблица**выберите таблицу в представлении источника данных, в которой находится столбец.  
  
4.  В разделе **Исходный столбец**выберите столбец, который необходимо добавить к структуре интеллектуального анализа данных.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  При добавлении уже существующего столбца в структуру будет включена копия, а к имени будет добавлена цифра 1. Можно изменить имя скопированного столбца на более наглядное, введя новое имя в качестве значения свойства **Имя** столбца структуры интеллектуального анализа данных.  
  
## <a name="see-also"></a>См. также  
 [Интеллектуального анализа данных структуры задачи и инструкции](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  

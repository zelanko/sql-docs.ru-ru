---
title: Добавление HTML в отчет (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 48b2f38635e77f58388cc6d3b04beedd7fdc470c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106622"
---
# <a name="add-html-into-a-report-report-builder-and-ssrs"></a>Добавление HTML в отчет (построитель отчетов и службы SSRS)
  С помощью заполнителя можно импортировать HTML из поля в наборе данных, чтобы использовать в отчете. По умолчанию заполнитель представляет простой текст, поэтому нужно изменить тип разметки заполнителя на HTML. Дополнительные сведения см. в разделе [Импорт HTML в отчет (построитель отчетов и службы SSRS)](importing-html-into-a-report-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-html-from-a-field-in-your-dataset-into-a-text-box"></a>Добавление HTML из поля набора данных в текстовое поле  
  
1.  На вкладке **Вставка** щелкните **Список**. Щелкните в области конструктора и перетащите указатель мыши, чтобы создать поле нужного размера.  
  
     Откроется диалоговое окно **Свойства набора данных** . Можно использовать общий набор данных или набор данных, внедренный в отчет. Чтобы получить дополнительные сведения, щелкните [Диалоговое окно "Свойства набора данных" — "Запрос" (построитель отчетов)](../report-data/dataset-properties-dialog-box-query-report-builder.md) или [Диалоговое окно "Свойства набора данных" — "Запрос"](../dataset-properties-dialog-box-query.md).  
  
2.  На вкладке **Вставка** щелкните **Текстовое поле**. Щелкните в списке и перетащите указатель мыши, чтобы создать поле нужного размера.  
  
3.  Перетащите в текстовое поле HTML-поле из набора данных. Для поля создается заполнитель.  
  
4.  Щелкните правой кнопкой мыши заполнитель и выберите пункт **Свойства местозаполнителя**.  
  
5.  На вкладке **Общие** убедитесь, что поле **Значение** содержит выражение, которое оценивается как поле, перемещенное на шаге 3.  
  
6.  Установите флажок **HTML — интерпретировать теги HTML как стили**. Тем самым поля будут вычисляться как HTML.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Форматирование чисел и дат (построитель отчетов и службы SSRS)](formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Форматирование линий, цветов и изображений (построитель отчетов и службы SSRS)](images-report-builder-and-ssrs.md)   
 [Диалоговое окно "Свойства заполнителя" — "Общие" (построитель отчетов и службы SSRS)](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  

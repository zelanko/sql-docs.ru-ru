---
title: Редактор преобразования соединения слиянием | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1f548972d99242a4bc3d3423eeed748de2c31704
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189018"
---
# <a name="merge-join-transformation-editor"></a>редактор преобразования «Cоединение слиянием»
  Диалоговое окно **Редактор преобразования «Соединение слиянием»** используется для задания типа соединения, столбцов соединения и выходных столбцов для слияния двух входных наборов с помощью соединения.  
  
> [!IMPORTANT]  
>  Преобразованию «Соединение слиянием» необходимы отсортированные входные данные. Дополнительные сведения об этом важном требовании см. в разделе [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Дополнительные сведения о преобразовании «Соединение слиянием» см. в разделе [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Тип соединения**  
 Укажите, нужно ли использовать внутреннее, левое внешнее или полное соединение.  
  
 **Обменять выходы**  
 Переключение порядка входов выполняется с помощью кнопки **Обменять выходы** . Этот выбор может быть полезен с параметром левого внешнего соединения.  
  
 **Ввод**  
 Вначале выберите из списка имеющихся входов каждый столбец, который необходимо включить в объединенный вывод.  
  
 Входы отображаются в двух отдельных таблицах. Выберите столбцы для включения в вывод. Перетащите столбцы для создания соединения между таблицами. Для удаления соединения выберите его и нажмите клавишу DELETE.  
  
 **Входной столбец**  
 Из списка имеющихся столбцов на выбранном входе выберите столбец для включения в объединенный вывод.  
  
 **Псевдоним вывода**  
 Введите псевдоним для каждого выходного столбца. По умолчанию, используется имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Сортировка данных для слияния и преобразования соединения слиянием](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [Расширение набора данных с помощью преобразование «Соединение слиянием»](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [Преобразование «Слияние»](data-flow/transformations/merge-transformation.md)   
 [Преобразование "Объединить все"](data-flow/transformations/union-all-transformation.md)  
  
  
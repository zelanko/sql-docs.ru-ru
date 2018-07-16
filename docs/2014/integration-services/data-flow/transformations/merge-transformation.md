---
title: Преобразование "Слияние" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bde18a7396d10ce15020e92d373239b8c3dd96c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215694"
---
# <a name="merge-transformation"></a>преобразование «Слияние»
  Преобразование «Слияние» объединяет два упорядоченных набора данных в один. Строки из каждого набора данных вставляются в выходной набор на основе значений их ключевых столбцов.  
  
 Включая преобразование «Слияние» в поток данных, можно выполнить следующие задачи:  
  
-   Произвести слияние данных из двух источников данных, таких как таблицы и файлы.  
  
-   Создать сложные наборы данных при помощи вложенных преобразований «Слияние».  
  
-   Произвести повторное слияние строк после исправления ошибок в данных.  
  
 Преобразование «Слияние» похоже на преобразование «Объединить все». Используйте преобразование «Объединить все» вместо преобразования «Слияние» в следующих случаях:  
  
-   Входы преобразования не упорядочены.  
  
-   Объединенный выход не требует упорядочения.  
  
-   Преобразование имеет более двух входов.  
  
## <a name="input-requirements"></a>Требования к входным данным  
 Преобразованию «Слияние» необходимы отсортированные входные данные. Дополнительные сведения об этом важном требовании см. в статье [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Кроме того, преобразование «Слияние» требует, чтобы у объединенных столбцов входных данных совпадали метаданные. Например, нельзя произвести слияние столбца числового типа данных со столбцом символьного типа. Если данные представляют собой тип строковых данных, длина столбца при вторичном входе должна быть меньше или равна длине столбца при первичном входе, с которым происходит слияние.  
  
 Пользовательский интерфейс для преобразования «Слияние» в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] автоматически сопоставляет столбцы с одинаковыми метаданными. Затем можно вручную сопоставить столбцы с совместимыми типами данных.  
  
 Это преобразование имеет два входа и один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-merge-transformation"></a>Настройка преобразования «Слияние»  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств.  
  
 Дополнительные сведения о параметрах, задаваемых в диалоговом окне **Редактор преобразования «Слияние»** , см. в разделе [Merge Transformation Editor](../../merge-transformation-editor.md).  
  
 Дополнительные сведения о параметрах, задаваемых программно, см. в следующих разделах:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Пользовательские свойства преобразований](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения о способах задания свойств см. в следующих разделах:  
  
-   [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>См. также  
 [Преобразование соединения слиянием](merge-join-transformation.md)   
 [UNION All Transformation](union-all-transformation.md)   
 [Поток данных](../data-flow.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  

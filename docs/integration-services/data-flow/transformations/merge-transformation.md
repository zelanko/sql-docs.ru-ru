---
title: Преобразование "Слияние" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.mergetrans.f1
- sql13.dts.designer.mergetransformation.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5badfcd6c8b9603e30e2a413bb6486fcf9d2c6b8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71291235"
---
# <a name="merge-transformation"></a>преобразование «Слияние»

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
 Преобразованию «Слияние» необходимы отсортированные входные данные. Дополнительные сведения об этом важном требовании см. в статье [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Кроме того, преобразование «Слияние» требует, чтобы у объединенных столбцов входных данных совпадали метаданные. Например, нельзя произвести слияние столбца числового типа данных со столбцом символьного типа. Если данные представляют собой тип строковых данных, длина столбца при вторичном входе должна быть меньше или равна длине столбца при первичном входе, с которым происходит слияние.  
  
 Пользовательский интерфейс для преобразования «Слияние» в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] автоматически сопоставляет столбцы с одинаковыми метаданными. Затем можно вручную сопоставить столбцы с совместимыми типами данных.  
  
 Это преобразование имеет два входа и один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-merge-transformation"></a>Настройка преобразования «Слияние»  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств.  
  
 Дополнительные сведения о параметрах, задаваемых программно, см. в следующих разделах:  
  
-   [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о способах задания свойств см. в следующих разделах:  
  
-   [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="merge-transformation-editor"></a>редактор преобразования «Слияние»
  **Редактор преобразования «Слияние»** используется для указания столбцов из двух отсортированных наборов данных для слияния.  
  
> [!IMPORTANT]  
>  Преобразованию «Слияние» необходимы отсортированные входные данные. Дополнительные сведения об этом важном требовании см. в статье [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
### <a name="options"></a>Параметры  
 **Имя выходного столбца**  
 Позволяет указать имя выходного столбца.  
  
 **Вход слияния 1**  
 Позволяет выбрать столбец в качестве входа слияния 1.  
  
 **Вход слияния 2**  
 Позволяет выбрать столбец в качестве входа слияния 2.  
  
## <a name="see-also"></a>См. также:  
 [Преобразование «Соединение слиянием»](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [Преобразование «Объединить все»](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  

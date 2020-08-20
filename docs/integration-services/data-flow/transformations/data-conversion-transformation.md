---
description: преобразование «Конвертация данных»
title: Преобразование "Конвертация данных" | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.dataconversiontrans.f1
- sql13.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cdd281be64879d56ec8c81eacc52ea3631fe0867
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477716"
---
# <a name="data-conversion-transformation"></a>преобразование «Конвертация данных»

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  При преобразовании «Конвертация данных» данные во входном столбце преобразуются в другой тип, а затем копируются в новый выходной столбец. Например, пакет может извлечь данные из нескольких источников, а затем с помощью этого преобразования привести столбцы к типу данных, требуемому целевым хранилищем данных. К одному входному столбцу можно применять несколько преобразований.  
  
 С помощью этой функции пакет может выполнять следующие типы преобразований данных:  
  
-   изменить тип данных; Дополнительные сведения см. в разделе [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Если данные преобразуются в тип данных даты или даты и времени, дата в выходном столбце имеет формат ISO, хотя специфические локали могут задавать другой формат.  
  
-   Задавать длину столбца строковых данных, а также точность и масштаб числовых данных. Дополнительные сведения см. в разделе [Точность, масштаб и длина (Transact-SQL)](../../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
-   Указать кодовую страницу. Дополнительные сведения см. в статье [Comparing String Data](../../../integration-services/data-flow/comparing-string-data.md).  
  
    > [!NOTE]  
    >  При выполнении копирования столбцов строкового типа данных оба столбца должны использовать одну и ту же кодовую страницу.  
  
 Если длина выходного столбца строковых данных меньше, чем длина соответствующего ему входного столбца, выходные данные усекаются. Дополнительные сведения см. в разделе [Обработка ошибок в данных](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Это преобразование имеет один вход, один выход и один выход ошибок.  
  
## <a name="related-tasks"></a>Связанные задачи  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств. Сведения об использовании преобразования "Конвертация данных" в конструкторе SSIS см. в разделе [Преобразование данных в другой тип данных с помощью преобразования "Конвертация данных"](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md). Сведения о настройке свойств этого преобразования программными средствами см. в разделах [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796) и [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
## <a name="related-content"></a>См. также  
 Запись в блоге [Сравнение производительности между способами преобразования типов данных в службах SSIS 2008](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035)на сайте blogs.msdn.com.  
  
## <a name="data-conversion-transformation-editor"></a>редактор преобразования «Конвертация данных»
  Используйте диалоговое окно **Редактор преобразования «Конвертация данных»** , чтобы выбрать столбцы, подлежащие преобразованию, выбрать тип данных, в который должен быть преобразован столбец, и установить атрибуты преобразования.  
  
> [!NOTE]  
>  Свойства **FastParse** выходных столбцов при преобразовании «Конвертация данных» недоступны в **Редакторе преобразования «Конвертация данных»**, но могут быть настроены при помощи **Расширенного редактора**. Дополнительные сведения о данном свойстве см. в подразделе «Преобразование "Конвертация данных"» раздела [Transformation Custom Properties](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
### <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Выберите столбцы, подлежащие преобразованию, установив флажки. Выбранные столбцы добавляются в качестве входных столбцов в таблицу, представленную ниже.  
  
 **Входной столбец**  
 Выберите столбцы, подлежащие преобразованию, из списка доступных входных столбцов. Выбранные пункты отражены набором установленных выше флажков.  
  
 **Псевдоним вывода**  
 Введите псевдоним для каждого нового столбца. Значением по умолчанию является **Copy of** , за которым следует имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
 **Тип данных**  
 Выберите доступный тип данных из списка. Дополнительные сведения см. в разделе [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 **Длина**  
 Установите ширину столбца для строковых данных.  
  
 **Точность**  
 Установите точность для числовых данных.  
  
 **Масштаб**  
 Установите масштаб для числовых данных.  
  
 **Кодовая страница**  
 Выберите подходящую кодовую страницу для столбцов типа DT_STR.  
  
 **Настройка вывода ошибок**  
 Укажите способ обработки ошибок уровня строк в диалоговом окне [Настройка вывода ошибок](https://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) .  
  
## <a name="see-also"></a>См. также  
 [Быстрый синтаксический анализ](https://msdn.microsoft.com/library/6688707d-3c5b-404e-aa2f-e13092ac8d95)   
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  

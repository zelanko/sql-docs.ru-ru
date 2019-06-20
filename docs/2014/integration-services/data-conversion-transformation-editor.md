---
title: Редактор преобразования для преобразования данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5346c808c7d724ae630bb3dd25016a9977af363e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66060044"
---
# <a name="data-conversion-transformation-editor"></a>редактор преобразования «Конвертация данных»
  Используйте диалоговое окно **Редактор преобразования «Конвертация данных»** , чтобы выбрать столбцы, подлежащие преобразованию, выбрать тип данных, в который должен быть преобразован столбец, и установить атрибуты преобразования.  
  
> [!NOTE]  
>  `FastParse` Свойство выходных столбцов преобразования «Конвертация данных» недоступно в **редактор преобразования для преобразования данных**, однако его можно установить с помощью **расширенный редактор**. Дополнительные сведения о данном свойстве см. в подразделе «Преобразование "Конвертация данных"» раздела [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Для более подробного знакомства с преобразованием «Конвертация данных» см. раздел [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Выберите столбцы, подлежащие преобразованию, установив флажки. Выбранные столбцы добавляются в качестве входных столбцов в таблицу, представленную ниже.  
  
 **Входной столбец**  
 Выберите столбцы, подлежащие преобразованию, из списка доступных входных столбцов. Выбранные пункты отражены набором установленных выше флажков.  
  
 **Псевдоним вывода**  
 Введите псевдоним для каждого нового столбца. Значением по умолчанию является `Copy of`, за которым следует имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
 **Тип данных**  
 Выберите доступный тип данных из списка. Дополнительные сведения см. в разделе [Integration Services Data Types](data-flow/integration-services-data-types.md).  
  
 **Длина**  
 Установите ширину столбца для строковых данных.  
  
 **Точность**  
 Установите точность для числовых данных.  
  
 **Масштаб**  
 Установите масштаб для числовых данных.  
  
 **Кодовая страница**  
 Выберите подходящую кодовую страницу для столбцов типа DT_STR.  
  
 **Настройка вывода ошибок**  
 Укажите способ обработки ошибок уровня строк в диалоговом окне [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование данных в другой тип данных с помощью преобразования «Конвертация данных»](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  

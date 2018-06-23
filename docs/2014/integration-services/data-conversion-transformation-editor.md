---
title: Редактор преобразования для преобразования данных | Документы Microsoft
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
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9c5157175181c7a43a2c8e3209c23905a4129d2d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097319"
---
# <a name="data-conversion-transformation-editor"></a>редактор преобразования «Конвертация данных»
  Используйте диалоговое окно **Редактор преобразования «Конвертация данных»** , чтобы выбрать столбцы, подлежащие преобразованию, выбрать тип данных, в который должен быть преобразован столбец, и установить атрибуты преобразования.  
  
> [!NOTE]  
>  `FastParse` Свойство выходных столбцов преобразования «Конвертация данных» недоступно в **редактор преобразования для преобразования данных**, но может быть задано с помощью **расширенный редактор**. Дополнительные сведения о данном свойстве см. в подразделе «Преобразование "Конвертация данных"» раздела [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Для более подробного знакомства с преобразованием «Конвертация данных» см. раздел [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Выберите столбцы, подлежащие преобразованию, установив флажки. Выбранные столбцы добавляются в качестве входных столбцов в таблицу, представленную ниже.  
  
 **Входной столбец**  
 Выберите столбцы, подлежащие преобразованию, из списка доступных входных столбцов. Выбранные пункты отражены набором установленных выше флажков.  
  
 **Псевдоним вывода**  
 Введите псевдоним для каждого нового столбца. Значение по умолчанию — `Copy of` за которым следует имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
 **Тип данных**  
 Выберите доступный тип данных из списка. Дополнительные сведения см. в статье [Integration Services Data Types](data-flow/integration-services-data-types.md).  
  
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
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование данных в другой тип данных с помощью преобразования "Конвертация данных"](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
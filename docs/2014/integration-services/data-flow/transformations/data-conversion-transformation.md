---
title: Преобразование "Конвертация данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b9bc5c7e4845adbc15d2e73d45ea85ff851084d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207544"
---
# <a name="data-conversion-transformation"></a>преобразование «Конвертация данных»
  При преобразовании «Конвертация данных» данные во входном столбце преобразуются в другой тип, а затем копируются в новый выходной столбец. Например, пакет может извлечь данные из нескольких источников, а затем с помощью этого преобразования привести столбцы к типу данных, требуемому целевым хранилищем данных. К одному входному столбцу можно применять несколько преобразований.  
  
 С помощью этой функции пакет может выполнять следующие типы преобразований данных:  
  
-   Изменить тип данных. Дополнительные сведения см. в статье [Integration Services Data Types](../integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Если данные преобразуются в тип данных даты или даты и времени, дата в выходном столбце имеет формат ISO, хотя специфические локали могут задавать другой формат.  
  
-   Задавать длину столбца строковых данных, а также точность и масштаб числовых данных. Дополнительные сведения см. в разделе [Точность, масштаб и длина (Transact-SQL)](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).  
  
-   Указать кодовую страницу. Дополнительные сведения см. в разделе [Comparing String Data](../comparing-string-data.md).  
  
    > [!NOTE]  
    >  При выполнении копирования столбцов строкового типа данных оба столбца должны использовать одну и ту же кодовую страницу.  
  
 Если длина выходного столбца строковых данных меньше, чем длина соответствующего ему входного столбца, выходные данные усекаются. Дополнительные сведения см. в разделе [Обработка ошибок в данных](../error-handling-in-data.md).  
  
 Это преобразование имеет один вход, один выход и один выход ошибок.  
  
## <a name="related-tasks"></a>Related Tasks  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств. Сведения об использовании преобразования "Конвертация данных" в конструкторе SSIS см. в разделах [Преобразование данных в другой тип данных с помощью преобразования "Конвертация данных"](data-conversion-transformation.md) и [Редактор преобразования "Конвертация данных"](../../data-conversion-transformation-editor.md). Сведения о настройке свойств этого преобразования программными средствами см. в разделах [Общие свойства](../../common-properties.md) и [Пользовательские свойства преобразований](transformation-custom-properties.md).  
  
## <a name="related-content"></a>См. также  
 Запись в блоге [Сравнение производительности между способами преобразования типов данных в службах SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823)на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также  
 [Быстрый синтаксический анализ](../../fast-parse.md)   
 [Поток данных](../data-flow.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  

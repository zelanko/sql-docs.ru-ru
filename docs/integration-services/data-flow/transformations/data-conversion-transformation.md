---
title: "Преобразование &#171;Конвертация данных&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataconversiontrans.f1"
helpviewer_keywords: 
  - "преобразование типов данных [службы Integration Services]"
  - "преобразование «Конвертация данных»"
  - "типы данных [службы Integration Services], преобразование"
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 53
---
# Преобразование &#171;Конвертация данных&#187;
  При преобразовании «Конвертация данных» данные во входном столбце преобразуются в другой тип, а затем копируются в новый выходной столбец. Например, пакет может извлечь данные из нескольких источников, а затем с помощью этого преобразования привести столбцы к типу данных, требуемому целевым хранилищем данных. К одному входному столбцу можно применять несколько преобразований.  
  
 С помощью этой функции пакет может выполнять следующие типы преобразований данных:  
  
-   Изменить тип данных. Дополнительные сведения см. в статье [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Если данные преобразуются в тип данных даты или даты и времени, дата в выходном столбце имеет формат ISO, хотя специфические локали могут задавать другой формат.  
  
-   Задавать длину столбца строковых данных, а также точность и масштаб числовых данных. Дополнительные сведения см. в разделе [Точность, масштаб и длина (Transact-SQL)](../../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
-   Указать кодовую страницу. Дополнительные сведения см. в разделе [Comparing String Data](../../../integration-services/data-flow/comparing-string-data.md).  
  
    > [!NOTE]  
    >  При выполнении копирования столбцов строкового типа данных оба столбца должны использовать одну и ту же кодовую страницу.  
  
 Если длина выходного столбца строковых данных меньше, чем длина соответствующего ему входного столбца, выходные данные усекаются. Дополнительные сведения см. в разделе [Обработка ошибок в данных](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Это преобразование имеет один вход, один выход и один выход ошибок.  
  
## Связанные задачи  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств. Сведения об использовании преобразования "Конвертация данных" в конструкторе SSIS см. в разделах [Преобразование данных в другой тип данных с помощью преобразования "Конвертация данных"](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md) и [Редактор преобразования "Конвертация данных"](../../../integration-services/data-flow/transformations/data-conversion-transformation-editor.md). Сведения о настройке свойств этого преобразования программными средствами см. в разделах [Общие свойства](../Topic/Common%20Properties.md) и [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
## См. также  
 Запись в блоге [Сравнение производительности между способами преобразования типов данных в службах SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823)на сайте blogs.msdn.com.  
  
## См. также  
 [Быстрый синтаксический анализ](../Topic/Fast%20Parse.md)   
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
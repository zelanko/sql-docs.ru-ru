---
title: "редактор преобразования &#171;Объединить все&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.unionalltransformation.f1"
helpviewer_keywords: 
  - "редактор преобразования «Объединить все»"
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# редактор преобразования &#171;Объединить все&#187;
  Для объединения нескольких входных наборов строк в один выходной набор строк используется диалоговое окно **Редактор преобразования «Объединить все»** . Включив преобразование «Объединить все» в поток данных, можно осуществлять слияние данных из нескольких потоков данных, создавать сложные наборы данных путем вложения преобразований «Объединить все» и повторно объединять строки после исправления ошибок данных.  
  
 Дополнительные сведения о преобразовании «Объединить все» см. в разделе [Union All Transformation](../../../integration-services/data-flow/transformations/union-all-transformation.md).  
  
## Параметры  
 **Имя выходного столбца**  
 Введите псевдоним для каждого столбца. По умолчанию, устанавливается имя входного столбца из первого (ссылочного) входного параметра, однако можно выбрать любое уникальное описательное имя.  
  
 **Вход 1 преобразования «Объединить все»**  
 Выберите из списка доступных входных столбцов в первом (ссылочном) входном параметре. Метаданные сопоставляемых столбцов должны совпадать.  
  
 **Вход n преобразования «Объединить все»**  
 Выберите из списка доступных входных столбцов во втором и дополнительных входных параметрах. Метаданные сопоставляемых столбцов должны совпадать.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Выполнение слияния данных с помощью преобразования «Объединить все»](../../../integration-services/data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Преобразование «Слияние»](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Преобразование «Соединение слиянием»](../../../integration-services/data-flow/transformations/merge-join-transformation.md)  
  
  
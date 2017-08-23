---
title: "UNION All Transformation | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 049d9195499e7145f98258cb90f2fd7069569058
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="union-all-transformation"></a>преобразование «Объединить все»
  Преобразование «Объединить все» объединяет несколько входов в один выход. Например, выходы из пяти различных источников неструктурированных файлов можно сделать входами для преобразования «Объединить все» и объединить в один выход.  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входы преобразования добавляются к выходу преобразования один за другим без переупорядочения строк. Если пакет требует сортировки выхода, то вместо преобразования «Объединить все» следует применять преобразование «Слияние».  
  
 Первый вход, подключенный к преобразованию «Объединить все» — это вход, из которого преобразование создает собственный выход. Входные столбцы, которые впоследствии будут подключены к преобразованию, сопоставляются со столбцами в выходе преобразования.  
  
 Для слияния входов нужно сопоставить входные и выходные столбцы. Необходимо, чтобы хотя бы один вход был сопоставлен каждому выходному столбцу. Сопоставление двух столбцов требует, чтобы метаданные этих столбцов совпадали. Например, сопоставленные столбцы должны относиться к одному и тому же типу данных.  
  
 Если сопоставленные столбцы содержат строковые данные, а длина выходного столбца меньше, чем длина входного, то выходной столбец автоматически увеличивается до нужной длины. Входные столбцы, не сопоставленные выходным столбцам, получают на выходных столбцах значения NULL.  
  
 Это преобразование имеет несколько входов и один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-union-all-transformation"></a>Настройка преобразования «Объединить все»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Объединить все»** , см. в разделе [Union All Transformation Editor](../../../integration-services/data-flow/transformations/union-all-transformation-editor.md).  
  
 Дополнительные сведения о свойствах, которые можно задать программно, см. в разделе [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796).  
  
 Дополнительные сведения о настройке свойств см. в следующих разделах.  
  
-   [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Выполнение слияния данных с помощью преобразования «Объединить все»](../../../integration-services/data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)  
  
  

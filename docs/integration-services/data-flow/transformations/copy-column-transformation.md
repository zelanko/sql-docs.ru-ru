---
title: "Преобразование «Копирование столбца» | Документы Microsoft"
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
- sql13.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3039b400b136b62840c40b463bb1d8f53a43251d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="copy-column-transformation"></a>преобразование «Копирование столбца»
  Преобразование «Копирование столбца» позволяет создавать новые столбцы путем копирования входных столбцов и добавления новых к выходу преобразования. На более поздних этапах потока данных к копиям столбцов могут применяться различные преобразования. Например, преобразование «Копирование столбца» можно использовать для создания копии столбца и дальнейшего перевода символов скопированных данных в верхний регистр с помощью преобразования «Таблица символов» или для статистической обработки нового столбца с помощью преобразования «Агрегатная обработка».  
  
## <a name="configuration-of-the-copy-column-transformation"></a>Настройка преобразования «Копирование столбца»  
 Преобразование «Копирование столбца» настраивается путем определения входных столбцов, которые необходимо скопировать. Можно создать несколько копий столбца или же копии нескольких столбцов в одной операции.  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Копирование столбцов»** , см. в разделе [Copy Column Transformation Editor](../../../integration-services/data-flow/transformations/copy-column-transformation-editor.md).  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
